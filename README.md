
**My-TRAC Data Model**

***Data Types***

| Type name | Description |
| --------- | ----------- |
| int | 32-bit integer |
| long | 64-bit integer |
| float | 32-bit floating point number |
| string | variable length string |
| timestamp | long containing epoch time in seconds |
| time | string with format "HH:MM:SS" |
| date | int with the form YYYYMMDD. Example 20180130 |
| enum | int representing an enumeration. Example 0 for bus, 1 for railway, etc. |

__For those conditionally required fields, please look at the official GTFS specification: https://gtfs.org/reference/static/ __

***Activity***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| activity_id | string | yes | My-TRAC |
| activity_name | string | yes | crawled |
| activity_lat | string | yes | crawled |
| activity_lon | float | yes | crawled |
| activity_type | string | yes | crawled |
| time_start | timestamp | yes | crawled |
| time_end | timestamp | yes | crawled |
| descriptors | string | no | My-TRAC |

***Agency***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| agency_id | string | yes | operators platform/gtfs |
| agency_name | string | yes | operators platform/gtfs |
| agency_url | string | yes | operators platform/gtfs |
| agency_timezone | string | yes | operators platform/gtfs |
| agency_lang | string | no | operators platform/gtfs |
| agency_phone | string | no | operators platform/gtfs |
| agency_fare_url| string | no | operators platform/gtfs |
| descriptors | string | no | My-TRAC |

***Calendar_Date***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| service_id | string | yes | operators platform/gtfs |
| date | date | yes | operators platform/gtfs |
| exception_type| enum | yes | operators platform/gtfs |

***Calendar***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| service_id | string | yes | operators platform/gtfs |
| monday | int | yes | operators platform/gtfs |
| tuesday | int | yes | operators platform/gtfs |
| wednesday | int | yes | operators platform/gtfs |
| thursday | int | yes | operators platform/gtfs |
| friday | int | yes | operators platform/gtfs |
| saturday | int | yes | operators platform/gtfs |
| sunday | int | yes | operators platform/gtfs |
| start_date | date | yes | operators platform/gtfs |
| end_date | date | yes | operators platform/gtfs |


***Facility***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| facility_id | string | yes | My-TRAC |
| facility_name | string | yes | crawled |
| facility_lat | string | yes | crawled |
| facility_lon | float | yes | crawled |
| facility_type | string | yes | crawled |
| descriptors | string | no | My-TRAC |

***Feed_Info***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| feed_published_name | string | yes | operators platform/gtfs |
| feed_published_url | string | yes | operators platform/gtfs |
| feed_lang | string | yes | operators platform/gtfs |
| feed_start_date | date | no | operators platform/gtfs |
| feed_end_date | date | no | operators platform/gtfs |
| feed_version | string | no | operators platform/gtfs |
| feed_contact_email | string | no | operators platform/gtfs |
| feed_contact_url | string | no | operators platform/gtfs |

***Frequency***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| trip_id | string | yes | operators platform/gtfs |
| start_time| time | yes | operators platform/gtfs |
| end_time | time | yes | operators platform/gtfs |
| headway_secs | int | yes | operators platform/gtfs |
| exact_times | enum | no | operators platform/gtfs |

***POI***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| poi_id | string | yes | My-TRAC |
| poi_type | string | no | crawled |
| poi_name | string | no | crawled |
| poi_lat | float | no | crawled |
| poi_lon | float | no | crawled |
| poi_amenity | string | no | crawled |
| descriptors | string | no | My-TRAC |

***Route***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| route_id | string | yes | operators platform/gtfs |
| agency_id | string | yes | operators platform/gtfs |
| route_short_name | string | yes | operators platform/gtfs |
| route_long_name | string | yes | operators platform/gtfs |
| route_desc | string | no | operators platform/gtfs |
| route_type | enum | no | operators platform/gtfs |
| route_type | enum | yes | operators platform/gtfs |
| route_url | string | no | operators platform/gtfs |
| route_color | string | no | operators platform/gtfs |
| route_text_color | string | no | operators platform/gtfs |
| route_sort_order | string | no | operators platform/gtfs |
| descriptors | string | no | My-TRAC |

***Shape***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| shape_id | string | yes | operators platform/gtfs |
| shape_pt_lat | float | yes | operators platform/gtfs |
| shape_pt_lon | float | yes | operators platform/gtfs |
| shape_pt_sequence | int | yes | operators platform/gtfs |
| shape_pt_sequence | int | yes | operators platform/gtfs |
| shape_dist_traveled | float | no | operators platform/gtfs |

***Stop_Time***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| trip_id | string | yes | operators platform/gtfs |
| arrival_time | time | no | operators platform/gtfs |
| departure_time | time | no | operators platform/gtfs |
| stop_id | string | yes | operators platform/gtfs |
| stop_sequence | int | yes | operators platform/gtfs |
| stop_headsign | string | no | operators platform/gtfs |
| pickup_type | enum | no | operators platform/gtfs |
| drop_off_type | enum | no | operators platform/gtfs |
| shape_dist_traveled | float | no | operators platform/gtfs |
| time_point | enum | no | operators platform/gtfs |
| descriptors | string | no | My-TRAC |

***Stop***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| stop_id | string | yes | operators platform/gtfs |
| stop_code | string | no | operators platform/gtfs |
| stop_name | string | no | operators platform/gtfs |
| stop_desc | string | no | operators platform/gtfs |
| stop_lat | float | no | operators platform/gtfs |
| stop_lon | float | nog | operators platform/gtfs |
| zone_id | string | no | operators platform/gtfs |
| stop_url | string | no | operators platform/gtfs |
| location_type | enum | no | operators platform/gtfs |
| parent_station | string | no | operators platform/gtfs |
| stop_timezone | string | no | operators platform/gtfs |
| wheelchair_boarding | string | no | operators platform/gtfs |
| level_id | string | no | operators platform/gtfs |
| descriptors | string | no | operators platform/gtfs |

***Transfer***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| from_stop_id | string | yes | operators platform/gtfs |
| to_stop_id | string | yes | operators platform/gtfs |
| transfer_type | enum | yes | operators platform/gtfs |
| min_transfer_time | int | no | operators platform/gtfs |

***Trip***

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| route_id | string | yes | operators platform/gtfs |
| service_id | string | yes | operators platform/gtfs |
| trip_id | string | yes | operators platform/gtfs |
| trip_headsign | string | no | operators platform/gtfs |
| trip_short_name | string | no | operators platform/gtfs |
| direction_id | int | no | operators platform/gtfs |
| block_id | int | no | operators platform/gtfs |
| shape_id | string | no | operators platform/gtfs |
| wheelchair_accessible | int | no | operators platform/gtfs |
| bikes_allowed | int | no | operators platform/gtfs |
| descriptors | string | no | operators platform/gtfs |
