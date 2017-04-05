{
  "timestamp" : "2017-04-05T13:40:34.191Z",
  "clusters" : [ {
    "name" : "vvaldevite",
    "version" : "CDH5",
    "services" : [ {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "1713373184"
          }, {
            "name" : "hive_metastore_server_max_message_size",
            "value" : "171337318"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "1713373184"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "3433247539"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "577"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "ip-172-31-8-114.us-west-2.compute.internal"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-470773506c5241e711e31ed02a27e3fb",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "1e49ab58-2fe6-4aab-b602-60f38fc30569"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-f397d2941be570f79b29026d2867af45",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "c5f09cff-29e9-4cff-a670-c58ef9b6da71"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-f962272e0617d558556fadb6f3d436de",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "76ae5bab-343c-48cd-ae2b-14ef9b1d71bc"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-676ee93aab427677c23c1649ec08ef9a",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "1ba8595a-143a-459e-a062-662ccd05cf83"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bsjshqsra4wokj13rj36i2pma"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-676ee93aab427677c23c1649ec08ef9a",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "1ba8595a-143a-459e-a062-662ccd05cf83"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8oitsq5lbobrb3o0kuk96bm6w"
          } ]
        }
      } ],
      "displayName" : "Hive"
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "SERVER",
          "items" : [ {
            "name" : "zookeeper_server_java_heapsize",
            "value" : "996147200"
          } ]
        } ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-676ee93aab427677c23c1649ec08ef9a",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "1ba8595a-143a-459e-a062-662ccd05cf83"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "atgh65x85v3tip8bbja096ix1"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-b4e26d7f440e4479241e7aeeede94b53",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "74da0eb8-6f72-4d74-9f8f-3afce6a5a3dc"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "881gxer14ef5zg6ba612k5vmy"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-f397d2941be570f79b29026d2867af45",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "c5f09cff-29e9-4cff-a670-c58ef9b6da71"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6lhjpnvr38868rzgols3lnqhl"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "ip-172-31-8-114.us-west-2.compute.internal"
        }, {
          "name" : "database_password",
          "value" : "hue"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-NAMENODE-676ee93aab427677c23c1649ec08ef9a"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-b4e26d7f440e4479241e7aeeede94b53",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "74da0eb8-6f72-4d74-9f8f-3afce6a5a3dc"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2icn8jk9dnn61nlmc1c92rtal"
          }, {
            "name" : "secret_key",
            "value" : "RLCEPutr6YC8Mv3roSu0gmOs2aPq6S"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "ip-172-31-8-114.us-west-2.compute.internal"
          }, {
            "name" : "oozie_database_password",
            "value" : "oozie"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          }, {
            "name" : "oozie_java_heapsize",
            "value" : "996147200"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-b4e26d7f440e4479241e7aeeede94b53",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "74da0eb8-6f72-4d74-9f8f-3afce6a5a3dc"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1mx1wj1i7966i3p812efd3z2"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "6"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "1"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "container_executor_allowed_system_users",
            "value" : "nobody,impala,hive,llama,hbase,vvaldevite"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "1800"
          }, {
            "name" : "rm_io_weight",
            "value" : "900"
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/data/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs,/data/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "4273"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "4939"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "90"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "Jb1PhnBRcIrrwwAaqaJb3KnTCmVY8H"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-676ee93aab427677c23c1649ec08ef9a",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "1ba8595a-143a-459e-a062-662ccd05cf83"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4ntmfctolni29gnbaxfwbu38p"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-470773506c5241e711e31ed02a27e3fb",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "1e49ab58-2fe6-4aab-b602-60f38fc30569"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8mh29v49kyyxcyt704ofl7fog"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-f397d2941be570f79b29026d2867af45",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "c5f09cff-29e9-4cff-a670-c58ef9b6da71"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5k4yydoi7orurg851zm8m1xj5"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-f962272e0617d558556fadb6f3d436de",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "76ae5bab-343c-48cd-ae2b-14ef9b1d71bc"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1si2q6jd3jn921r1naa9v18x9"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-676ee93aab427677c23c1649ec08ef9a",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "1ba8595a-143a-459e-a062-662ccd05cf83"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "92"
          }, {
            "name" : "role_jceks_password",
            "value" : "7b2k9qweeefwchreorsc64eau"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/data/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "4293264998"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "200"
          }, {
            "name" : "rm_io_weight",
            "value" : "100"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "JOURNALNODE",
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/journal"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/data/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "namenode_java_heapsize",
            "value" : "996147200"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/data/dfs/snn"
          }, {
            "name" : "secondary_namenode_java_heapsize",
            "value" : "996147200"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "qFgtdIROwkeFT3KtLohSDKEUEMuZAb"
        }, {
          "name" : "dfs_ha_fencing_methods",
          "value" : "shell(true)"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "EduMDlGLFZGjwAsp4tYzSEcERvxWKH"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "bKyUiiSj1bZtdesLIyTfRKwrnnkAeT"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "10"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-676ee93aab427677c23c1649ec08ef9a",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "1ba8595a-143a-459e-a062-662ccd05cf83"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-470773506c5241e711e31ed02a27e3fb",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "1e49ab58-2fe6-4aab-b602-60f38fc30569"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cwwwn6bwhykr16vyf36zfjaw3"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-f397d2941be570f79b29026d2867af45",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "c5f09cff-29e9-4cff-a670-c58ef9b6da71"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2760z6zvlunx99jfpvkbk0rxt"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-f962272e0617d558556fadb6f3d436de",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "76ae5bab-343c-48cd-ae2b-14ef9b1d71bc"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "65lgrqfub8kjcbu9g7dqpn4dm"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-676ee93aab427677c23c1649ec08ef9a",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "1ba8595a-143a-459e-a062-662ccd05cf83"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "c48eagdu3a46jvwturlwap6b8"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-b4e26d7f440e4479241e7aeeede94b53",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "74da0eb8-6f72-4d74-9f8f-3afce6a5a3dc"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "6immwuxuicwoxp0it3xrlaeid"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-676ee93aab427677c23c1649ec08ef9a",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "1ba8595a-143a-459e-a062-662ccd05cf83"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cvpkc0xr583cx6c88l7fx0tq3"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-b4e26d7f440e4479241e7aeeede94b53",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "74da0eb8-6f72-4d74-9f8f-3afce6a5a3dc"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1d0027barnce92k5bmfyutkjg"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-f962272e0617d558556fadb6f3d436de",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "76ae5bab-343c-48cd-ae2b-14ef9b1d71bc"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8gus93gp5bagbpvjqan3as2z3"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-676ee93aab427677c23c1649ec08ef9a",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "1ba8595a-143a-459e-a062-662ccd05cf83"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "94"
          }, {
            "name" : "role_jceks_password",
            "value" : "awnfe09uopxxo0ld80536xfoi"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-b4e26d7f440e4479241e7aeeede94b53",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "74da0eb8-6f72-4d74-9f8f-3afce6a5a3dc"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "101"
          }, {
            "name" : "role_jceks_password",
            "value" : "8299kdkpmphgbai14zty3mng2"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "1e49ab58-2fe6-4aab-b602-60f38fc30569",
    "ipAddress" : "172.31.15.123",
    "hostname" : "ip-172-31-15-123.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "c5f09cff-29e9-4cff-a670-c58ef9b6da71",
    "ipAddress" : "172.31.2.15",
    "hostname" : "ip-172-31-2-15.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "76ae5bab-343c-48cd-ae2b-14ef9b1d71bc",
    "ipAddress" : "172.31.5.59",
    "hostname" : "ip-172-31-5-59.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "74da0eb8-6f72-4d74-9f8f-3afce6a5a3dc",
    "ipAddress" : "172.31.7.135",
    "hostname" : "ip-172-31-7-135.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "1ba8595a-143a-459e-a062-662ccd05cf83",
    "ipAddress" : "172.31.8.114",
    "hostname" : "ip-172-31-8-114.us-west-2.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-b4e26d7f440e4479241e7aeeede94b53",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "b6166a89ecfaa690a091a8c787b531fb0b033ccbbb0b10a6014adbf110f6927a",
    "pwSalt" : 7042239649866179066,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-b4e26d7f440e4479241e7aeeede94b53",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "84bbbfd5eda5b548676d9439accb64e9d475eec4241c1dd214ff49454b030c04",
    "pwSalt" : -5826190154239321484,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-b4e26d7f440e4479241e7aeeede94b53",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "2189e137a9b606b329c694fb0c5f77d44b70c0d0efd688059323738dae12215d",
    "pwSalt" : -5826751285565061216,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-b4e26d7f440e4479241e7aeeede94b53",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "0faf5a6d352806a825bc687daf3988979226a2a2106523790822503ead0b40ce",
    "pwSalt" : 3588456249201825374,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "433840c35dbd60c572b2eb326a39fa11a879337a5795e5ab27e551de5f13db47",
    "pwSalt" : 1755646198676136420,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "f78f2250114cadd16fbb23ad3f228ba75d92bf795dd5d45f1304b3d8d8ded247",
    "pwSalt" : -6089208071467161480,
    "pwLogin" : true
  }, {
    "name" : "vvaldevite",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "218700faaf787d2f69b159aa52f5bb13f7403f8ea2d3a036cb8112290f6a9e05",
    "pwSalt" : 8316769823144779083,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.10.1",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20170319-2001",
    "gitHash" : "f226435f6fa5f545543c00245900ae43bea7a29c",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "EVENTSERVER",
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "995098624"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "995098624"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1293942784"
        }, {
          "name" : "firehose_storage_dir",
          "value" : "/data/var/lib/cloudera-host-monitor"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "ip-172-31-7-135.us-west-2.compute.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        }, {
          "name" : "headlamp_heapsize",
          "value" : "995098624"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "995098624"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1293942784"
        }, {
          "name" : "firehose_storage_dir",
          "value" : "/data/var/lib/cloudera-service-monitor"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ALERTPUBLISHER-b4e26d7f440e4479241e7aeeede94b53",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "74da0eb8-6f72-4d74-9f8f-3afce6a5a3dc"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "30mx24fqkm8ufdjysgju1jbt4"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-b4e26d7f440e4479241e7aeeede94b53",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "74da0eb8-6f72-4d74-9f8f-3afce6a5a3dc"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "elgi5sq5swjkzzek1yq2g8tpi"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-b4e26d7f440e4479241e7aeeede94b53",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "74da0eb8-6f72-4d74-9f8f-3afce6a5a3dc"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "af5kr4f25pw39h720m245iw55"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-b4e26d7f440e4479241e7aeeede94b53",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "74da0eb8-6f72-4d74-9f8f-3afce6a5a3dc"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "bzec22mlm4u9469xgqtirhw5r"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-b4e26d7f440e4479241e7aeeede94b53",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "74da0eb8-6f72-4d74-9f8f-3afce6a5a3dc"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "7sqqhpd330f3tmz6d91lxa7zq"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/26/2012 7:20"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "http://ip-172-31-7-135/cdh5.10/"
    } ]
  }
}