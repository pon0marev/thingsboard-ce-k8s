Create reaper keyspace

Update cassandra deployment file and apply it.

CREATE KEYSPACE IF NOT EXISTS reaper_db WITH replication = {'class': 'NetworkTopologyStrategy', 'datacenter1': 3 };

fort forward
kubectl port-forward svc/cassandra-reaper 8080
http://localhost:8080/webui/


(optional) Fixing IP seeds on the cluster settings
use reaper_db;
select * from cluster;
UPDATE reaper_db.cluster SET seed_hosts = {'cassandra'} WHERE name = 'thingsboard_cluster';