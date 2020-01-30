# Lark IT Ansible AWS EC2 Role

Creates and ecnrypted AWS RDS PostgreSQL instance, subnet group, and security group. Scheduled maintenance, scheduled snapshots, and final snapshot are enabled by default. 

## Dependencies
- Assumes a VPC and 3 subnets exist, preferablly one subnet per AZ
- Assumes a KMS key to encrypt the instnace exists
- This role is not dependent on any other roles

## Variables
| Variable | Required? | Default Value | Type | Description |
|----------|-----------|---------------|------|-------------|
| rds_ingress_sg_name | Yes | N/A | String | The name of the security group that will be granted access to the RDS instance | 
| rds_subnet_names | Yes | N/A | List | A list of subnet names for RDS instance subnet group | 
| rds_kms_key_name | Yes | N/A | String | The name of the KMS key used to encrypt the RDS instance |
| rds_name | Yes | N/A | String | The name of the RDS instance | 
| rds_engine | No | postgres | String | The database engine to use on the RDS instance |
| rds_engine_version | No | 11 | String | The version of the database engine to use on the RDS instance |
| rds_instance_class | Yes | N/A | String | The RDS instance size or type |
| rds_allocated_storage | Yes | N/A | Int | The size of the RDS instance storage in Gigabytes |
| rds_db_name | Yes | N/A | String | The name of the database |
| rds_db_username | Yes | N/A | String | The database master username | 
| rds_db_password | Yes | N/A | String | The database master pasword |
| rds_backup_retention_period | No | 7 | Int | The number of days to retain scheduled snapshots |  
| rds_preferred_backup_window | No | 07:00-08:00 | String | The scheduled snapshot window |
| rds_preferred_maintenance_window | No | Sun:09:00-Sun:10:00 | String | The scheduled maintenance window |
