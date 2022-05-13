# R-UDP

# **Running the program in terminal**:
```
sudo docker-compose up -d 
```

```
sudo docker-compose exec receptor bash -c "python3 /elocal/src/server.py -p 10000 -f /elocal/src/date.out" 
```

```
sudo docker-compose exec emitator bash -c "python3 /elocal/src/client.py -a 198.8.0.2 -p 10000 -f /elocal/src/date.in" 
```
