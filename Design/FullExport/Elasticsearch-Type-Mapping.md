
#  **Overview**  :
 Type mapping inside  **elasticsearch**  can be dynamic or static. Both mapping has it's own pros and cons. For initial usage dynamic mapping is fine, because we won't have complete knowledge of data model and it's usability. But for production, dynamic mapping upper limit can get consumed very quickly.

 **Problem statement :** Sunbird currently is using dynamic mapping for  **elasticsearch**  indexes., Inside Elastic search default index limit is  **1000.** So if your index reached 1000 limit , then it won't allow any other key to be indexed.

Sunbird platform has reached this limit, and introduction of new key would throw error.

 **Solution 1:**        Use of static mapping, where static mapping can be of two type.


*   **Flexible static mapping** :  In this case first time we can define all attribute and it's type, and elasticseaerch will do indexing for only those attribute ,which is already defined in mapping, and it will allow user to store other attribute as well without indexing
*  **Strict mapping** :  In this case first time we can define all attribute and it's type, and elasticseaerch will do indexing for only those attribute ,which is already defined in mapping, and it will throw error if any new attribute is introduced.

 **Syntax for enabling above strategies:** 

 **Flexible static mapping:**  { "dynamic": false, "properties": { } }

 **Strict static mapping:** { "dynamic": "strict", "properties": { } }

 **Solution 2:** Use of dynamic mapping and adjust the keep increasing the upper limit as target is reached. 

We can increase limit of index form 1000 to 1500  as follow:


```js
Method : PUT
http://localhost:9200/searchindex/settings 
  
 Request body :
 { "index.mapping.totalfields.limit": 1500 }

```

## Curl command to do mapping:

```js
Method : Put  
http://localhost:9200/searchindex/batch/_mapping 
  {
  "dynamic": false,
  "properties": {
    "all_fields": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower"
        }
      },
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer"
    },
    "countDecrementDate": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "countDecrementStatus": {
      "type": "boolean",
      "fields": {
        "raw": {
          "type": "boolean"
        }
      }
    },
    "countIncrementDate": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "countIncrementStatus": {
      "type": "boolean",
      "fields": {
        "raw": {
          "type": "boolean"
        }
      }
    },
    "courseCreator": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "courseId": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "batchId": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "createdBy": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "createdDate": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "createdFor": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "description": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "endDate": {
      "type": "date",
      "fields": {
        "raw": {
          "type": "date"
        }
      }
    },
    "enrollmentType": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "hashTagId": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "id": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "identifier": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "mentors": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "name": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    },
    "startDate": {
      "type": "date",
      "fields": {
        "raw": {
          "type": "date"
        }
      }
    },
    "status": {
      "type": "long",
      "fields": {
        "raw": {
          "type": "long"
        }
      }
    },
    "updatedDate": {
      "type": "text",
      "fields": {
        "raw": {
          "type": "text",
          "analyzer": "keylower",
          "fielddata": true
        }
      },
      "copy_to": [
        "all_fields"
      ],
      "analyzer": "cs_index_analyzer",
      "search_analyzer": "cs_search_analyzer",
      "fielddata": true
    }
  }
}
```



## Course batch mapping details:


| Old | New | 
|  --- |  --- | 
| { "dynamic_templates": \[ { "longs": { "match_mapping_type": "long", "mapping": { "fields": { "raw": { "type": "long" } }, "type": "long" } } }, { "booleans": { "match_mapping_type": "boolean", "mapping": { "fields": { "raw": { "type": "boolean" } }, "type": "boolean" } } }, { "doubles": { "match_mapping_type": "double", "mapping": { "fields": { "raw": { "type": "double" } }, "type": "double" } } }, { "dates": { "match_mapping_type": "date", "mapping": { "fields": { "raw": { "type": "date" } }, "type": "date" } } }, { "strings": { "match_mapping_type": "string", "mapping": { "analyzer": "cs_index_analyzer", "copy_to": "all_fields", "fielddata": true, "fields": { "raw": { "type": "text", "fielddata": true, "analyzer": "keylower" } }, "search_analyzer": "cs_search_analyzer", "type": "text" } } } ], "properties": { "all_fields": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower" } }, "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer" }, "countDecrementDate": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "countDecrementStatus": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "countIncrementDate": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "countIncrementStatus": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "courseAdditionalInfo": { "properties": { "courseLogoUrl": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "courseName": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "description": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "leafNodesCount": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "status": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "tocUrl": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true } } }, "courseCreator": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "courseId": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "createdBy": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "createdDate": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "createdFor": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "description": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "endDate": { "type": "date", "fields": { "raw": { "type": "date" } } }, "enrollmentType": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "hashTagId": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "hashtagid": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "id": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "identifier": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "mentors": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "name": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "participant": { "properties": { "006ee23c-4575-4e84-bf12-6b0742fc37c2": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "00809309-b0e7-47c3-9363-4e2e43a37906": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "00a70eea-5b99-4638-af5f-043a941fea21": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "016cd1bf-445f-434e-b28d-c7b5c7f59de7": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "01dbd988-ca3e-448f-aeb7-8e93cefe994d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "021093d8-9ddc-4fce-825d-353161ec1107": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "044976d2-00d6-4b67-8f24-219098ddd40f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "04b26947-0995-4d8a-9e37-9a38443b5338": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0525d460-3696-4e87-a5db-d5ff5b095014": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "05cd6783-f70b-4cc2-b920-f0a188c38bba": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "05d7d9e3-c916-4f59-a81c-95ec58f18599": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0731e7dc-1699-4873-b513-750d1944b868": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "081f5324-4090-4916-a968-e3f18b6cd795": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "084e6be5-945e-4e35-8be8-b2344e403f4f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "08915a50-a8b9-428e-8e26-8c46efe25f5d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0936cd2f-9343-4581-8d21-66dd5998bd53": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "09b9e982-8633-4023-8843-e636d0cf11e9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0a32e459-93ac-4825-a7d6-835794c1c184": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0a4e9612-92f8-42b2-a995-a8915d4f6d51": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0ab81e6e-77d6-4eeb-bfe8-a9864d17dfbd": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0ac395d2-0806-4932-9498-b2c2100f1dc4": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0b3794ee-3f0d-4584-b08e-c10ae49dc4dc": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0b65cf79-7624-4c0d-8cde-9d34a28ddf58": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0c383526-2677-46be-8fb0-06d41392d40b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0c6aefd8-c50a-43e2-8b40-b9c57dd95f3b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0d5a9409-4b25-4b64-9d1b-b908829448af": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0d7c6d15-749f-4b61-91c7-ace6007e752d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0d8ee43c-338e-4ab1-b47b-08d444eb282e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0edd8df6-6829-473a-b8bd-d5d0fc95c643": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0f8afc90-d069-496f-9dd8-04c0ab831ae4": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0f8e6b8d-bbc9-4d04-99c1-b97ca8f4780f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "0fb08dc4-05b9-4828-9e48-a7e753c9264b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "105ab834-5b0f-4d8a-8a60-94c2e5150b08": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "106b99ab-a3bc-4f3e-bb05-94030bba9ae6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "10b9b330-dd12-4888-8faa-1e4bd3fa1a2b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "1145efbf-e397-4906-9be1-9417e7f5c57d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "1153a0ed-3d36-424f-9245-deb14ce5ae81": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "11f850a7-9f90-419a-b45d-eefe035167f5": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "12228bdd-bf6c-4f55-851c-e840acc4c324": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "12232318-7520-496b-b6f3-a9bd4d71a771": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "1307fe6d-698a-4a3d-8d3f-095eea85cad6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "140eae8d-fd07-4dc8-8582-4001e448eb94": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "14df02ff-7e68-4c52-a600-1b1f30c62ffe": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "150c315b-3672-4baa-9037-8a1eece3c827": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "159e93d1-da0c-4231-be94-e75b0c226d7c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "15dedad5-1332-4618-824f-63d859a662fd": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "160cdb40-792c-445a-81fc-2271818ac14f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "163d4fc0-43a8-4590-8243-4236a149ad68": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "1811fb1b-b2ea-4250-9780-66b72ffd2d40": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "19507f7d-6edc-40ac-9fad-d866e285873b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "1a6bee12-5661-4493-acc3-a5f4aeb36ac8": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "1a7d4ec2-11f7-40e3-a1cf-0d88603e392c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "1ae66368-ffee-4f31-b9f8-9356b01cf9e3": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "1b025783-d404-4b01-8367-1637a245279c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "1ba87afa-310c-476d-879c-5e5a92a6a1ae": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "1ca43e90-a0ea-4eb8-9ae1-d2976a636045": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "1f1524d7-3d21-41e8-abfc-833a3749a86b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "20022a84-2774-4a58-8005-e49651fe9186": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "20d546a7-5715-4511-9c43-08f2b54a09c3": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "212cbf1e-9aee-41ff-b137-3a1d54fd8bee": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "22782071-1f6d-45d9-89b8-951020e8c212": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "22c5b3be-22c1-4ca3-a220-41c83b529996": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "22c7c2ba-b8ff-45ec-81ef-604e235a3e6d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "22f2f83c-e9d2-4332-a02e-979026624a64": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "230cb747-6ce9-4e1c-91a8-1067ae291cb9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "23bf659b-1f5a-473a-9228-3be519a29004": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "24822e18-c0b9-44a8-9140-855186670553": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "26199785-e8ed-4537-88fe-a25183d8a240": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "27d5a117-e1a1-4202-8476-6be21fd76a5c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "281609c4-6f02-48e4-be74-e0d109940592": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "28f7bf03-68be-4d62-b794-23040eada4e1": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "28fee419-2e24-4f9f-8090-ed736fca5844": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "29286780-1a14-489d-a244-d8c2f8019e53": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "299a91db-c08b-40c3-806e-2aecfc58ec5b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2a1e364f-13e4-4657-b29b-842982926366": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2a25480b-03f1-4772-80a1-dc65bb002e3c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2a3454fe-7d73-4f4d-874e-4a8d4fc7c190": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2a6bde34-0e89-4182-b717-fe6d8faf849f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2af668b3-9de6-4c25-8589-adf41ca420d4": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2bad9be5-4bae-4e94-8f9e-55e3a28c3535": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2c467bbb-6316-4f16-8e04-45c10fbc72ac": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2c617525-0a8c-41d2-a453-703af9b5cb2d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2ce6bf93-f084-44ad-bf43-bc6c618a7efa": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2d7ef8e4-5452-435b-8c8d-a135a1fe003d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2e5383e7-11ec-4b76-be38-0dc722676845": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2e54c55f-c530-479d-b133-8673e5437b66": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2e941094-a8b4-4b70-acef-38ae743153cf": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2f0c4567-7cec-4d7d-b0a6-2e06d7277df1": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "2fa5ba9c-6048-4975-a469-9f2632fea1eb": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "30aaa06e-948e-4608-9827-e47080e7e488": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "311a5845-b391-4af9-89e0-744b13534a4c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "31544209-6b02-4756-88cf-94a304b117ce": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "32f52c6a-0d66-48a7-88bb-a7e87774b7e1": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "34b7f441-851e-445c-90aa-434604216851": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "36d3af69-73d7-41a8-b315-23992cb265f8": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "36fff1f2-1c78-4e4b-addd-719d3d5534a8": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "376f9444-7a42-435d-b360-61b72e220070": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "37b7f6f2-28c3-48a2-95b4-c5f12bba4b86": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3806bd5a-73fa-4742-b2c1-e73aaa36579b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3806e346-47b1-4301-95f4-eb35ba52cef9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3859df3b-75f7-4bc5-8914-0a03e22c2567": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3a15e710-b1c3-4eee-84b1-5de5a59b752a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3b284205-405f-47f3-bae8-3438989076d9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3b34c469-460b-4c20-8756-c5fce2de9e69": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3be5ec51-44d8-41d9-973d-f2d932841c76": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3becd312-737c-4192-8c69-c01146b8a80e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3c562a96-cbab-4fa9-823f-2563d1c38daf": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3ca152a2-7ca4-4170-8e52-90f6684f4b64": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3d45fbd8-b911-4cc5-b503-61215902d780": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3de0f5a0-4863-4286-b773-6294a1c1dc27": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3e6c6eb7-8c0c-45b6-9114-e36b59e1aa8b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "3f678f46-ef8b-4cc5-a037-667c521c1d26": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "40862b8d-e9ef-4cd6-b9bd-645930304c99": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "40c2022b-d81c-43d0-a6bf-e6005cb97315": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "40e6d5ff-00d1-4e2c-9e1f-72451dc544bc": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4192642d-f2fa-4080-948f-f0cd5df88f61": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "419ac78e-c12f-4358-b8d9-495dbb1794ba": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "427c4723-7fd1-4b8a-a49f-7af635e288a9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "433199eb-26f1-4da3-9cc2-9a858c182033": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "43ac79b8-e6c6-4023-b945-fb0ae9daee7d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "43e30ac4-8576-4c06-a372-b20f816a5079": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4480049b-0ec4-4534-a48b-7660f766f68d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "44c3a14c-d9b3-4269-ab28-946418de4030": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "44d898f6-9f58-45df-aec6-1bdcf518b8d6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "45d73314-b014-47a7-979b-f3b25a2513bf": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "47324bc4-6604-4cfe-8f78-9d0af2c49b5b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4759e4c7-96a2-4857-a3ea-359f74077cc9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "47bea1c9-8dc2-4270-b9e0-e0212cc5c7f7": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "48cff933-aee6-4096-ba66-b5736b08b482": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "492e3f9b-2d6f-4686-9e60-a748f39fd9a6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4af283c2-0748-465d-ab85-51cd33d91ee2": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4b3f1210-9b6d-4309-833e-523c4d26ac21": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4b5c6fdc-4eae-4547-9685-c82de34008fb": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4c62f335-baa3-47c2-aadd-aeb182e8b219": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4cab13f2-6b86-46f9-9ed8-13b20022f1c9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4cabe52d-9195-4629-b6d9-677e89c77e1f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4cb25361-6893-423d-aab7-6bc98992db9f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4d26100b-0cf0-46ba-b64e-0696083ae73f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4db43f0f-dd63-4491-a231-11c2a1b366fa": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4e034bc4-4077-403d-bd33-0e8147b533b4": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4e4c4c3d-19e4-4c6e-b0ea-171a62387fa2": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4e79190d-3f9d-4473-8c8e-e5b3c9f49dd0": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "4f72702e-1a12-4974-b6cc-894ed657dc24": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "508b44d2-b3ef-49cf-9ae3-c4c4a9d6e39a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5136a8fb-4e0c-4b28-9172-21840d0e65b8": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5205332d-3693-40e4-88fc-4025f1c1d6fb": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "522753ce-12ad-47fc-9a2c-65657b788a8c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "52308223-da6b-45c7-9520-4e8c526e6c22": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "523da72c-2491-4bb0-95c0-974a71df525f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "539af117-e300-4fb7-89b4-891fccece95c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "53c463cc-8594-431c-9c82-bb212acb510a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "53f97e0c-ee7e-4ff6-b18c-ad892cea609b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "54b3bdc1-7dca-42d7-872a-0bf19522483a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "550b23de-2c1c-42b5-964d-140cd4b4e695": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "557b06bf-db38-4a0b-b8ab-459122f0163d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "55fefcb5-c602-4190-863a-40c8c21104a0": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "561429bb-fd85-4a83-a80d-a04a5f7c3eee": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5681bb50-9058-4733-b47d-cb93981eb441": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "56d45538-9971-4024-b2a0-a37c066b57a6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5789c637-cb52-419d-8949-d5944bf3e46c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "57c3d12d-c4f6-4293-b8cc-2517bec630cd": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "586e35db-7938-4aa8-8e64-0cb690cc0caf": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "591e231c-f247-43a8-b27b-4017db0a98c6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "59ad77af-ea93-44fa-8c87-9e24fa497860": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "59f0a539-658d-441e-bf01-48599e2a55ce": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5a8c0bdf-96a3-402d-a761-6af4a1ef4447": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5af6fe1e-e4a0-44f4-a074-fdd7e051e695": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5b95b9b8-16eb-4e9a-a335-74a202b8fcc6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5b9abe66-f3eb-425f-a169-06eb7e7035b3": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5b9db00c-a92b-4238-a7ec-e5cb2965891a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5c127b9e-24f6-4f63-b4d7-2253980df354": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5c6aa24f-0c9f-483b-9f8b-6413305b1155": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5cc24df9-45dc-467a-8b40-562631a084ca": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5d4a846b-a588-4b99-9aa7-52eb4df7066f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5d7eb482-c2b8-4432-bf38-cc58f3c23b45": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5de150a5-2cf9-4bda-99fd-61539e888e51": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5deffd51-fe32-4a83-8b47-a2e940afd9a2": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5e2c5c35-4130-43ec-b52f-893560a2814b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5e546fb9-23d5-4bba-a252-851779f04693": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5e8832cf-ea48-4319-96de-c61097a6b200": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5ef0bebf-7571-4e5a-87ac-7599d9ab786d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "5fa88456-f8ee-464e-87cb-d1973a494242": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6075afa9-f7ee-4317-a1d8-ea075bbc02b7": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "60c614a2-2742-40ae-b9f9-db46c2b11457": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "612bd881-edce-414b-9ea9-df79dbdd12f3": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "619e58ac-021a-4796-92be-9cb9698d184e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6201fb10-a4e0-4cf3-911c-859501b165bb": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6220d9c2-79f5-4471-b3da-1d5082dedc4b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "62354c16-29c7-419c-8d30-a30491bef7c3": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "62d46bfa-48fb-4858-a625-7f80b3c66915": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "62f9a4f5-3146-4a13-8a83-f6ae8df4c20e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "63867eaa-191b-42d4-8de5-441d5b669dca": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "63bfe373-f9c8-43d6-91c6-b5e97c9502e0": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "646f3c3b-ef22-4b99-9567-46b51ed2303c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "659545c9-3d29-45b2-9297-b8168661d746": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "65f5490c-af60-4c86-a091-37db5dacbfc5": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "66b793a7-7ab1-4f98-be4e-5973b69e7870": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6721e33a-9cbb-4c5b-8069-b6236ac98bcd": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6724959c-917e-4a72-89f3-a454f94eb3f6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "68bc780b-84de-47c0-aaf8-d522a2a1e96d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "68c67a3b-9799-4e89-acaa-2c48681c486d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6ac242f7-5325-4fdb-8a0e-270557e4748d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6b0f554a-6ef8-4388-b87c-ffcb9d8bcd62": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6b6fcf86-d6e8-4042-8f9b-7e65d57e6337": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6b8e5d81-9ed0-40f9-851b-5e6d66ed852b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6c3d25b3-ae5f-492a-88c7-c336d0efdc09": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6cb8bfd1-1ab9-4d36-a515-ded9eac9d63b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6cba29d9-beac-4fd9-8abd-40c2e6cfbe4f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6d4da241-a31b-4041-bbdb-dd3a898b3f85": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6d881143-6fb6-49c3-b237-61e9fc7bb5b6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6e01ca97-41bb-4f7f-8eaf-99ed408aeb8a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6e0c52df-d475-4fb7-a8da-7a31f9529635": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6e4fa739-84b9-47ea-9758-914e0b967697": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6e850e7c-cae0-417a-8ca6-cd042905c568": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6ebccbac-6840-4b04-afbf-c448abf70609": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6eec9cd5-14ef-4ba3-8767-72721305a718": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6f3897a4-29d9-4a37-b4cb-5ad6c64ac3c5": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "6fc5cb95-4536-4a5f-b381-a83fc934f7a8": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "70191df3-d3a0-43b3-91aa-23b7eeefc8fe": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "7073aa92-64ed-43a2-aab1-5358080ff135": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "7074d213-fb3e-41f1-9aa1-76410060e56f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "728dbf44-79ce-40bb-9e2e-c27ca9befb82": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "72d07fd7-9363-4e6f-804b-af8ec99cc2bf": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "72f5fb7a-a374-41b5-a26d-9e51b538b38a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "731d39be-41b5-41c6-af22-275fd94417d2": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "7764641e-7019-4d9b-a28a-c6777ed606ca": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "7811968a-0456-48ab-a798-db897be27385": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "781c21fc-5054-4ee0-9a02-fbb1006a4fdd": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "799a2d87-5741-485c-a25c-b844ce4ad73d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "79bdcb03-df4a-4392-916b-303cff769da2": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "7a2599be-ae01-44d1-8916-b9d22ef49639": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "7a586f72-3f71-46c6-86a9-fc0e8cd21b50": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "7c1668c0-3f5d-4731-be1a-85f1b0b5251c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "7c168fe1-b5a6-41f2-bd9f-723f45200c60": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "7c3c218d-c494-4e3e-954d-bd940e769a7e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "7d7411e6-aa06-42da-a390-43915b0ca528": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "7dd39831-66fe-468f-97e0-ca158203375a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "7e1f42b5-c41e-4d19-b969-2cb7c08be02e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "80075c12-61e2-4c71-a9ed-e4494cdea379": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "805d896d-89b3-41d5-8df3-bed994b217a1": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "80f318e4-a735-4d08-bd74-55c4b937c8db": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "811aabb2-cae2-48f2-8348-0d4c09a15524": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "81b38a6c-db25-4680-9a90-776dd0b8e0f9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8410a69e-31dd-47b1-a89e-186fccb3e352": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8454cb21-3ce9-4e30-85b5-fade097880d8": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "84d85d96-3b9b-4711-8abc-07f60312c8ef": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8557fa44-6b3a-4a4a-bb99-7907e635b2f7": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "85b57399-085d-4cd3-9192-9b80ebda649f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "85f6a663-e4ee-4d6c-9b46-8facce4d99cc": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8677187e-af21-46a4-8acc-0e5838efcd89": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "874ed8a5-782e-4f6c-8f36-e0288455901e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "877c28e7-5b8b-4586-a999-ff768d66562c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "87b8ef8f-988f-4ef5-9221-81c11ddfcfb1": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "88488283-0837-44dd-90a8-82f3b5eea699": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "88bc10ef-e7cd-40e9-b94d-9ecf15f0152d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "88dfe8e5-2ec4-4feb-a9cf-617c5f0b4ffa": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "897dd2fc-16c6-41bf-a217-6969c036dd5b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8b79899c-573f-44ed-a0a2-e39d9299bf20": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8baa4ff7-f035-4d0e-b700-0eae8ed6f126": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8bca909a-ef99-400d-af6e-dbc13ddc577d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8bf991b8-5ddd-434f-b1c5-aea8caaa20e6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8d39d450-117f-4b82-aa3a-cf6eb3708186": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8d6fd426-46a0-49db-8970-8d1aea434e58": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8dee0600-6627-40fa-ab4c-070c493b5a0a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8efb7238-08ce-4b92-b71e-d3c194f9c75a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "8f61d566-0131-45f3-924b-ab8cc7f3d1c9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "9047586d-736b-4438-8f72-4ef37e8fc1f5": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "912d6b7d-3561-42a9-9216-5c22b53c6ba0": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "914334ee-e88b-4283-98a0-f96911110bdf": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "91d8b6e9-bc21-4c6b-a2bf-d6f506dba2fe": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "92933265-7b1e-44bb-8d08-42cad41bac59": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "93e02dd0-0ff0-4838-9fe0-2342b688e27c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "94291a0d-3e90-4530-a00e-a960b3873727": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "95a6af4b-0ab9-4d15-a83e-2ae086075c05": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "95e4942d-cbe8-477d-aebd-ad8e6de4bfc8": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "9645e749-39f0-4b73-993d-09e633eeea1d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "96d2f097-3f82-4d83-97de-79a58356a254": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "97255811-5486-4f01-bad1-36138d0f5b8a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "977e36b9-608c-4794-a9fa-0bcec899143c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "97d81cb6-a348-42f1-91ba-150961a74444": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "9a570c3a-df73-49b0-8697-ddc74efcbee8": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "9b3e3f7c-34e6-4a9a-8759-6f6ade230887": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "9b8b1833-4e7a-48a3-bc11-49aee1386771": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "9c2d3022-8a2b-4279-bc31-c60f5a55e2a4": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "9c4983d1-b374-4dbc-89bc-e70d79347abf": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "9cfa76ba-7b15-4821-8f32-0f49876372fd": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "9d76c081-fbf6-45e0-adb7-64013fe41a64": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "9f02c51f-6907-40fe-849c-9b74831868e6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "9fdaffa4-206e-4452-a060-9cffae9f5565": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a01d2c45-4807-4e76-9f1b-ca6a20fd21c5": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a049605f-a632-4b57-93cb-0e6189847ebc": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a1978a18-e612-450d-8238-330a61236ed5": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a2c70e63-51fb-4066-8efb-83d4d26240d6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a3b219d9-a61f-4e69-b26c-688054b204c4": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a3d0af06-e1ad-4cbf-96af-bad1e28a5f98": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a3d4151b-4d3e-4068-8950-d5b27b10487e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a41d7abc-5325-4fbe-b3a2-38c5a6220ce9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a56c1977-195e-41ac-b687-81f80e85e6f4": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a624f6ee-1d5c-469f-ba86-94259b90c13b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a67c9237-ed59-4a87-b5fc-bc343ea62299": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a742aa23-0b32-4cf5-be6f-02a05b75fe5d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a7b76f1d-7ea9-41b1-b61c-c551f54b5a7a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a7d400b1-347f-4afe-9034-8e3f53a34185": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a80b5136-e2d5-4b7a-be55-74c3867717a9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a8798265-a639-41fc-a11f-658746741ab2": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a8b2e156-6b63-4c8b-a492-d2979a5b9553": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a9e297be-e8ab-4690-983a-251748fb143e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "a9e6e188-4887-49ca-99af-b17802f2343a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ab0ec3a9-5235-46da-83a7-ab74baa384bb": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ac918519-f8b8-4150-bd90-56ead42454d0": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ade0dc06-c67c-46e2-bd74-ee6821116775": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "af72ce38-f0b0-40ad-bd31-1e87545f4cff": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b111ca73-e3f1-4b0d-8fa2-15c95fe7769f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b1208ad8-631f-4d1a-916b-05ddfe305032": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b14e7747-e66d-49f3-8152-7a6706f0b530": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b15b345f-b532-466f-96e8-948545e3220b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b1af9a9d-cab2-4859-90d1-eaec34a9b4cd": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b1c1feff-1917-4bbf-85ee-f81a81fbc01b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b1c5f3e6-6a8f-4466-9bcf-1244f3c51e29": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b2479136-8608-41c0-b3b1-283f38c338ed": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b2ba0548-9bcb-4486-90ac-5fa33be0d4ba": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b5ec0bfb-ac7f-4767-9308-8cfbdfc18706": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b6222540-61f8-46cf-bac9-ebcc357c2418": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b7608667-fcc2-4be6-bf74-ae77ca484826": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b78ea480-be16-430f-b31b-c897a362674d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b7b20414-15d4-4566-ac43-f958b763c40f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b8567249-1bcc-460d-85d7-0b1d4f0902a6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b8a1637a-6f72-4639-bf01-808b25cf3e47": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b8cd0907-4f8e-4ea8-8555-b3a39179a2e5": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b902c1bb-2eda-45b1-bbf9-0d9d680226e3": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b910cb07-b195-478e-a936-df8ac3289642": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "b95f2688-f1c7-4f45-bcf7-08a9563b4645": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ba817300-5422-4028-83c3-d9971e48d033": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "bab1fca2-7c80-4be0-a527-a5dec91694f6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "bacacc74-f828-403c-987a-333550c204db": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "bb005f9e-0ac8-4b39-a97a-6b82e9209cd3": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "bb407bfb-1478-4d26-85d2-6742f57fe8d8": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "bd525cc6-318e-497a-9a3f-3a9e169cf7e7": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "be15b62d-14d0-482e-93ad-5ec0e7f84c38": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "be325d93-600d-4cb2-b2c9-728717c31765": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "be3e2e35-247c-4de0-a4e4-ae1e57078cf6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "be68c555-7e9b-4cd8-a2ac-4e172f1bfe5b": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "bedf24a5-68a3-47dd-b13a-77bd508e5b47": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "bf06f2af-49b1-4669-9680-7fc90c6f468a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "bf851834-466c-427a-8e00-d6a55c4ada8a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c06222b0-e17e-4763-a8e9-371f30e51886": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c0d5a8ae-707c-4c67-84e5-b87b0048b7fc": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c1bcccac-63ac-4053-9096-9a11b9fd8c37": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c20290b9-1624-4beb-960b-23eeff652694": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c24a59f9-662a-44dc-b0f4-6cf0bfac4522": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c2570075-e6df-4b8b-84a6-a15b92087a97": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c42f7544-be83-43c2-abf5-9217b0919ba4": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c4e09a90-adcb-498d-a8d1-837f730b4504": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c6a16e2a-3d48-47db-8595-bece1aedb251": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c6cf3b11-475a-456f-a8a1-ac27416553df": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c6d95527-e795-441c-aeeb-b79315c06432": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c6f02b71-4ef6-4450-96f8-0d173f67f33f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c7107542-7b20-4a74-b9b9-f35e35b57a08": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c7e35899-2ed1-47ad-9338-b1d8e2170483": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c858ca1b-d604-49d5-b3b7-9356405ee304": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c8735bc1-29cc-4d3b-9754-0d8e52f96b5e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c87dc61a-3a0b-4ac2-a473-9a1122046fac": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c89c0a8e-e6d2-49e2-99cb-6e568b473261": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c93bcd0c-3034-4f88-ae0d-310aabfbdf57": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "c94d3c51-7cb4-4e4e-a1fb-b418160bd1f9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "cac7fbc5-1425-49d5-843a-a734f4e5d107": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "cb2636bb-a848-4c9d-9ac8-767ba1f04717": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "cb9425ce-b917-4aca-b720-012f25c30999": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "cbdd80a1-44b1-4889-a779-8f732be75b31": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "cc1615d1-bf96-4d2c-881d-7a76da9e6cf5": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "cc935cd8-d4aa-4d67-8f9d-5827449490da": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "cce46da5-d632-4cb7-b617-fa28ca58551f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "cd03dd47-2096-4296-be65-3670b91ae715": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ce5fd84f-9f7d-4c8f-9375-01fe94f420f3": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "cfc7b772-2d14-4df1-b83c-c80764b22b9a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d0708400-68c4-468e-99bd-9758e4247b57": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d0c8ce38-2cda-48a9-ae72-a62e28202c9f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d161799a-ffe1-4e92-b575-e95328f3190e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d174e049-fbe4-469e-bb21-26c0c66152c0": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d1924601-9ce1-4b6e-b3b1-1442a3d61ac4": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d1eba4ca-7056-47d6-a052-90edfbae7727": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d20925cc-aad7-4b89-a674-c05d957e4854": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d26d1138-e5e1-4b31-b93b-eeb9e2b8c945": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d56a1766-e138-45e9-bed2-a0db5eb9696a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d5efd1ab-3cad-4034-8143-32c480f5cc9e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d625e47b-de95-49c4-a08c-4f0f9b21c052": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d88c5a91-ce4c-44c4-b39a-cb2ecd929452": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d933b129-2959-466d-acb2-0e0b03963919": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d95ae83d-8277-4fc9-8b43-7e9ee5f5d142": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d9d92812-45f3-4759-90ec-ad4bd233cd91": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "d9f0e530-193c-4214-a6e5-7601202b24c6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "da266895-8710-469c-902e-16999b8b33c4": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "da2ee489-a4fd-4382-a16f-162443a4ded0": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "da98666f-3f21-4251-9f36-746bc70836a7": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "dba6a3be-e3aa-4d0f-9c20-3bb9356522e7": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "dbc49243-d7c6-4116-bb1b-2bf629ccf8be": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "dbd37223-9732-4377-bc81-cbad4238024e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "dcccc201-d591-4131-9650-a380367d450e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ddea8816-ee89-4f25-974f-1af54b39f156": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "de213b94-576e-49aa-a573-c02fac07a109": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "de9a619f-d621-41b8-aefb-00859e1655e8": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "df337721-d88e-4d99-8d88-5a0b51d50141": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "df6f285a-531c-4fed-bb54-6cc8235968f4": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e044a0a2-0c4a-4c1e-bfba-7500c2d94152": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e0a58ad5-9da8-47fa-a331-b1de45f28d13": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e0ba193b-3cd6-46d3-9719-e11f293c8088": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e0cac18a-a352-468a-b4e0-76b411d86d36": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e335b263-1d1d-44de-aa4d-ea9248847d54": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e3d2b80e-78e1-4913-b55a-d52c7dcd102d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e4455303-2d66-400c-88ad-92e57aa844af": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e45517df-f8a7-44df-9830-32a8dc20cd6c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e4d8e4b3-6d75-4cef-88f4-204e3cf917c5": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e4dc2c2d-aa7d-4178-9c8b-dc57855c8900": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e53bfde4-d82d-4a50-bc35-d6250814338d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e556cd9c-1567-482a-aef2-1f235c8ed985": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e5f61eeb-73e3-42db-bc3a-68e33f51589e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e61d399a-9d55-4b13-b036-612b1e9c4762": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e652e039-ea4c-43d6-8056-00e773a176b9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e65909e4-68e2-4aff-a8f3-c69d90611f3d": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e6fd0283-2c42-4365-a60f-16b73f64ef6a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e7592ce3-4605-4a3c-82cb-158951b0903c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e77cfde4-8849-479c-a8cc-791b99c66993": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e865c53b-4e2a-4d99-8398-02af6ad5c794": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "e97aba85-f89b-4e26-809a-3b8092267be5": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ea647670-e4ac-4cb5-8fc9-9d2f5a4479b7": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "eb234478-fe80-4673-aaed-2b8dc91d481c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ebaa622f-3864-43de-aa6f-f5c1723a7674": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ec4452bd-e33c-4de5-acb0-ca4a12f8c269": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ed7ab534-e17c-47ea-a62b-c3e8822099e6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ed8609b2-95d4-4464-9ed3-58f0e56b929a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "eea56eb3-9ce0-4efd-9e58-18c261d010c0": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "eefd3dd4-2ba9-48e5-b089-cf0e531d22d9": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f0a3ad9a-32be-4359-9574-80d5caece2bc": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f0b782d0-2132-4825-beb9-ad0fc1bb44d8": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f0f056f3-01a6-4d46-8283-55db4b13b825": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f0f3ecf3-3cf0-4c4c-a3a8-d998acd6ef13": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f1e82b9e-0f2e-4e1c-aef4-7bb5ca653f47": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f2071d05-894e-4c6b-8b37-34a1bc078dcd": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f2eea64e-0e93-444f-b81b-05ea5bad32ba": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f2f1fb2e-6acd-41dd-9b10-f65e2f7a4ef8": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f339d867-c95d-43d2-a65b-2b2ec805a545": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f36d0e72-f703-40dd-bbd3-465a9dc1b8d6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f3db903e-b29f-4cd3-a686-cd262fcd7e82": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f3e9ba0e-9109-4d73-a82f-6ac4e7679568": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f427fc72-05ac-4b8d-8d6c-9219517552cd": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f44f94ca-a61c-4bbd-bad7-bff44d4c548a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f61831b9-1b0e-46dd-9ede-3127451b86ff": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f622a01e-d38d-4110-b283-90c50478409a": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f66eafc1-b180-428d-9425-b1335fcf8425": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f6ce9726-a022-48fc-8157-1b43d3401760": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f7909acb-85c4-4747-9cc3-e69f2aaadc01": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f9003c0b-c6cf-4e97-8896-27b989f86726": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "f9f92618-c9ac-4534-9148-0eab00dbfc15": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "faac1b45-393f-4dcb-a6af-9171e6ded3ed": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "fae8f720-51a6-48cb-8834-33641a42c30e": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "fbf1a5e2-955f-4172-9c10-277cb1c0d7f3": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "fc024150-c2f9-40ae-9713-23a6fee1941c": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "fc594e97-23b7-41ad-88d1-fc49904b93f1": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "fc69eeef-bed1-426a-8023-7dc939c3ea0f": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "fc95a3e5-4092-4478-ac5c-cf54b5e56ae5": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "fcc1c08e-6aaa-4087-a562-d1a1779be182": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ff9a37c3-0364-4360-9de9-b0f9e5af39ac": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "ffac8e0a-4594-4339-87af-2f8fc1317fe6": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "someUserId": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } } } }, "participants": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "startDate": { "type": "date", "fields": { "raw": { "type": "date" } } }, "status": { "type": "long", "fields": { "raw": { "type": "long" } } }, "updatedDate": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true } } } | { "dynamic": false, "properties": { "all_fields": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower" } }, "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer" }, "countDecrementDate": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "countDecrementStatus": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "countIncrementDate": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "countIncrementStatus": { "type": "boolean", "fields": { "raw": { "type": "boolean" } } }, "courseCreator": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "courseId": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "batchId": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "createdBy": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "createdDate": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "createdFor": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "description": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "endDate": { "type": "date", "fields": { "raw": { "type": "date" } } }, "enrollmentType": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "hashTagId": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "id": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "identifier": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "mentors": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "name": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true }, "startDate": { "type": "date", "fields": { "raw": { "type": "date" } } }, "status": { "type": "long", "fields": { "raw": { "type": "long" } } }, "updatedDate": { "type": "text", "fields": { "raw": { "type": "text", "analyzer": "keylower", "fielddata": true } }, "copy_to": \[ "all_fields" ], "analyzer": "cs_index_analyzer", "search_analyzer": "cs_search_analyzer", "fielddata": true } } } | 




## Mapping definition storage : 
Mapping definition can be store as follow:


1.  Storage in cassandra (Example : corresponding each type will store mapping as well)
1.  Storing in resource file : Create a json file that will have type name and mapping data.







-- New Mapping files

250250250250250250250

-- Old Mapping files:

250250250250250250250250250250250250




### Problem Statement
How to manage the mapping of indexes?


### Solution Approach
The mapping can be stored in database and can be updated and invoked through API. Whenever someone invokes an API for updating mapping, it is first stored in DB and then makes an internal call to Elasticsearch to update mapping.

Table structure

| column | type | description | 
|  --- |  --- |  --- | 
| index | text  | name of the index, partition key | 
| type  | text | the type for which the mapping should be applied, primary key | 
| version | int | part of primary key, can be used for auditing or getting current mapping | 
| mapping | text | the json of mapping called | 
| status | int | denotes 1 for success, 0 for failure | 
| response | text | response received from ES while calling update mapping | 
| createdBy | text | userId of person who called update mapping API | 
| createdOn | timestamp | when the API was invoked to update mapping | 



API Structure
```js
Request
 
PUT /es/index/{indexName}/mapping
{
  "type": "_doc",
  "mapping": {
       	"dynamic": false,
  		"properties": {
    		"all_fields": {
      			"type": "text",
      			"fields": {
        			"raw": {
          				"type": "text",
          				"analyzer": "keylower"
        			}
      			},
      			"analyzer": "cs_index_analyzer",
      			"search_analyzer": "cs_search_analyzer"
    		},
    		"name": {
      			"type": "text",
      			"fields": {
        			"raw": {
          				"type": "text",
          				"analyzer": "keylower",
          				"fielddata": true
        				}
      				},
      			"copy_to": [
        			"all_fields"
      			],
      			"analyzer": "cs_index_analyzer",
      			"search_analyzer": "cs_search_analyzer",
      			"fielddata": true
    		}
		}
	}
  }
}
 
Response
 
{
  "id": "api.es.index.mapping",
  "result": {
		"response" : {
				// response from ES
			} 
	}
}
```










*****

[[category.storage-team]] 
[[category.confluence]] 
