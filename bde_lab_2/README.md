docker run -dit --rm --name cassandra -v ~/Projects/big_data_eng/bde_lab_1/data:/var/lib/cassandra cassandra:3.11

docker run -dit --rm --name bde_mongo \
    -v ~/Projects/big_data_eng/bde_lab_1/data:/data/db \
    -e MONGO_INITDB_ROOT_USERNAME=mongo \
    -e MONGO_INITDB_ROOT_PASSWORD=mongo \
    -p "27017:27017" \
    mongo:4.2 \
    --bind_ip_all
