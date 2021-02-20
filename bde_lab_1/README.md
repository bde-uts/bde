

docker run -dit --rm --name bde_lab_1 -p 5432:5432 -e POSTGRES_PASSWORD=bde_lab_1 -v ~/Projects/big_data_eng/bde_lab_1/data:/var/lib/postgresql/data postgres:11