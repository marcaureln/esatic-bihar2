ARG jdkVersion=11

FROM openjdk:${jdkVersion}

COPY . /opt

WORKDIR /opt

# Find the only .tar.gz file and set it as an environment variable
RUN export kvliteArchive=$(ls *.tar.gz) \
    && if [ $(echo $kvliteArchive | wc -w) -ne 1 ]; then echo "Error: There should be exactly one .tar.gz file"; exit 1; fi \
    && gunzip $kvliteArchive \
    && tar -xvf ${kvliteArchive%.gz} \
    && mv kv-* kv \
    && rm ${kvliteArchive%.gz}

WORKDIR /opt/kv

EXPOSE 5000
EXPOSE 8000

ENV KV_SECURE_MODE=enable
ENV KV_STORAGE_DIR_SIZE=5

CMD java -Xmx64m -Xms64m -jar lib/kvstore.jar kvlite -host 0.0.0.0 -port 5000 -admin-web-port 8000 -secure-config "$KV_SECURE_MODE" -storagedirsizegb "$KV_STORAGE_DIR_SIZE"
