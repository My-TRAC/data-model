
# My-TRAC Data Model

## Data Types

| Type name | Description | MY-SQL type (Minimum version 5.7) |
| --------- | ----------- | ----------- |
| boolean | A boolean | TINYINT |
| int | 32-bit integer | INT |
| long | 64-bit integer | BIGINT |
| float | 32-bit floating point number | FLOAT |
| double | 64-bit floating point number | DOUBLE |
| string | variable length string | VARCHAR(256) |
| timestamp | string with format YYYY-MM-DD hh:mm:ss | TIMESTAMP(3) |
| time | string with format "hh:mm:ss" | TIME(3) | 
| date | int with the form YYYYMMDD. Example 20180130 | INT | 
| enum | int representing an enumeration. Example 0 for bus, 1 for railway, etc. | INT |
| json | string representing a JSON | JSON |

__For those conditionally required fields, please look at the official GTFS specification: https://gtfs.org/reference/static/__

## Data Items

These represent the different items in the My-Trac data model. There is a one-to-one mapping between items and tables, and these can be synchronized by individual components' My-SQLs.

### activity

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | MyTrac Activity Crawler |
| mytrac_is_valid | boolean | yes | MyTrac Activity Crawler |
| mytrac_last_modified | timestamp | yes | MyTrac Activity Crawler |
| activity_creation_date | timestamp | yes | MyTrac Activity Crawler | 
| activity_id | string | yes | crawled |
| activity_name | string | yes | crawled |
| activity_lat | double | yes | crawled |
| activity_lon | double | yes | crawled |
| activity_type | enum | yes | crawled |
| activity_start | timestamp | yes | crawled |
| activity_end | timestamp | yes | crawled |
| activity_timezone | string | yes | crawled |
| activity_reputation | double | yes | MyTrac-Companion |


activity_type enum can have the following values:
* 0: work/out-of-office
* 1: education
* 2: health
* 3: service
* 4: religion
* 5: history/culture
* 6: hobby
* 7: eating & drinking
* 8: shopping

### agency (Operator)

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | operators portal |
| mytrac_is_valid | boolean | yes | operators portal |
| mytrac_last_modified | timestamp | yes | operators portal |
| agency_id | string | yes | operators portal/gtfs |
| agency_name | string | yes | operators portal/gtfs |
| agency_url | string | yes | operators portal/gtfs |
| agency_timezone | string | yes | operators portal/gtfs |
| agency_lang | string | no | operators portal/gtfs |
| agency_phone | string | no | operators portal/gtfs |
| agency_fare_url| string | no | operators portal/gtfs |

### calendar_date

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | operators portal |
| mytrac_is_valid | boolean | yes | operators portal |
| mytrac_last_modified | timestamp | yes | operators portal |
| service_id | string | yes | operators portal/gtfs |
| date | date | yes | operators portal/gtfs |
| exception_type| enum | yes | operators portal/gtfs |

### calendar

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | operators portal |
| mytrac_is_valid | boolean | yes | operators portal |
| mytrac_last_modified | timestamp | yes | operators portal |
| service_id | string | yes | operators portal/gtfs |
| monday | int | yes | operators portal/gtfs |
| tuesday | int | yes | operators portal/gtfs |
| wednesday | int | yes | operators portal/gtfs |
| thursday | int | yes | operators portal/gtfs |
| friday | int | yes | operators portal/gtfs |
| saturday | int | yes | operators portal/gtfs |
| sunday | int | yes | operators portal/gtfs |
| start_date | date | yes | operators portal/gtfs |
| end_date | date | yes | operators portal/gtfs |


### facility

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | operators portal |
| mytrac_is_valid | boolean | yes | operators portal |
| mytrac_last_modified | timestamp | yes | operators portal |
| facility_id | string | yes | My-TRAC |
| facility_name | string | yes | crawled |
| facility_lat | double | yes | crawled |
| facility_lon | double | yes | crawled |
| facility_type | enum | yes | crawled |

### feed_info

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | operators portal |
| mytrac_is_valid | boolean | yes | operators portal |
| mytrac_last_modified | timestamp | yes | operators portal |
| feed_published_name | string | yes | operators portal/gtfs |
| feed_published_url | string | yes | operators portal/gtfs |
| feed_lang | string | yes | operators portal/gtfs |
| feed_start_date | date | no | operators portal/gtfs |
| feed_end_date | date | no | operators portal/gtfs |
| feed_version | string | no | operators portal/gtfs |
| feed_contact_email | string | no | operators portal/gtfs |
| feed_contact_url | string | no | operators portal/gtfs |

### frequency

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | operators portal |
| mytrac_is_valid | boolean | yes | operators portal |
| mytrac_last_modified | timestamp | yes | operators portal |
| trip_id | string | yes | operators portal/gtfs |
| start_time| time | yes | operators portal/gtfs |
| end_time | time | yes | operators portal/gtfs |
| headway_secs | int | yes | operators portal/gtfs |
| exact_times | enum | no | operators portal/gtfs |

### mobility_trace

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | My-Trac Companion |
| mytrac_is_valid | boolean | yes | My-Trac Companion |
| mytrac_last_modified | timestamp | yes | My-Trac Companion |
| user_id | string | yes | My-Trac Companion |
| trace_lat| double | yes | My-Trac Companion |
| trace_lon | double | yes | My-Trac Companion |
| trace_prov | string | yes | My-Trac Companion |
| trace_time | timestamp | yes | My-Trac Companion |
| trace_acc | float | no | My-Trac Companion |
| trace_alt | float | no | My-Trac Companion |
| trace_bear | float | no | My-Trac Companion |
| trace_bear_acc | float | no | My-Trac Companion |
| trace_speed | float | no | My-Trac Companion |
| trace_speed_acc | float | no | My-Trac Companion |
| trace_vert_acc | float | no | My-Trac Companion |


### otp_reply

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | My-Trac Companion |
| mytrac_is_valid | boolean | yes | My-Trac Companion |
| mytrac_last_modified | timestamp | yes | My-Trac Companion |
| choice_id | string | yes | My-Trac Companion |
| request_reply | json | yes | MyTrac-Companion |
| region | enum | yes | MyTrac-Companion |
| model_api | enum | yes | MyTrac-Companion |
| num_itineraries | int | yes | My-Trac Companion |

region enum can have the following values:
* 1: Dutch
* 2: Hellenic
* 3: Portuguese
* 4: Spanish
* 5: Other

model_api enum can have the following values:
* 1: Default
* 2: Choice
* 3: Departure
* 4: Personalistation


### poi

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | My-TRAC |
| mytrac_is_valid | boolean | yes | My-TRAC |
| mytrac_last_modified | timestamp | yes | My-TRAC |
| poi_id | string | yes | My-TRAC |
| poi_type | enum | yes | crawled |
| poi_name | string | yes | crawled |
| poi_lat | double | yes | crawled |
| poi_lon | double | yes | crawled |
| poi_amenity | string | yes | crawled |
| poi_reputation | double | yes | MyTrac-Companion |

poi_type enum can have the following values:
* 0: work/out-of-office
* 1: education
* 2: health
* 3: service
* 4: religion
* 5: history/culture
* 6: hobby
* 7: eating & drinking
* 8: shopping


### poll_questionary

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | My-TRAC |
| mytrac_is_valid | boolean | yes | My-TRAC |
| mytrac_last_modified | timestamp | yes | My-TRAC |
| poll_id | long | yes | MyTrac-Companion |
| questions | json | yes | MyTrac-Companion |
| type | string | yes | MyTrac-Companion |
| lang | string | yes | MyTrac-Companion |


### poll_response

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | My-TRAC |
| mytrac_is_valid | boolean | yes | My-TRAC |
| mytrac_last_modified | timestamp | yes | My-TRAC |
| user_id | string | yes | MyTrac-Companion |
| poll_questionary_mytrac_id | long | yes | MyTrac-Companion |
| responses | json | yes | MyTrac-Companion |


### route

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | operators portal |
| mytrac_is_valid | boolean | yes | operators portal |
| mytrac_last_modified | timestamp | yes | operators portal |
| route_id | string | yes | operators portal/gtfs |
| agency_id | string | yes | operators portal/gtfs |
| route_short_name | string | conditional | operators portal/gtfs |
| route_long_name | string | conditional | operators portal/gtfs |
| route_desc | string | no | operators portal/gtfs |
| route_type | enum | no | operators portal/gtfs |
| route_type | enum | yes | operators portal/gtfs |
| route_url | string | no | operators portal/gtfs |
| route_color | string | no | operators portal/gtfs |
| route_text_color | string | no | operators portal/gtfs |
| route_sort_order | string | no | operators portal/gtfs |

### route_choice_model_output

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | My-Trac Companion |
| mytrac_is_valid | boolean | yes | My-Trac Companion |
| mytrac_last_modified | timestamp | yes | My-Trac Companion |
| choice_id | string | yes | My-Trac Companion |
| trip_dur_car | int | yes | My-Trac Companion |                            
| trip_dur_pt | int | yes | My-Trac Companion |                                     
| trip_dur_moto | int | yes | My-Trac Companion |                       
| trip_dur_bike | int | yes | My-Trac Companion |
| trip_comfort_car | int | yes | My-Trac Companion |                        
| trip_comfort_pt | int | yes | My-Trac Companion |                         
| trip_comfort_moto | int | yes | My-Trac Companion |               
| trip_comfort_bike | int | yes | My-Trac Companion |            
| trip_cost_car | float | yes | My-Trac Companion |                          
| trip_cost_moto | float | yes | My-Trac Companion |                        
| trip_cost_bike | float | yes | My-Trac Companion | 
| trip_cost_pt | float | yes | My-Trac Companion |
| mod_car | float | yes | Mode Choice Model |
| mod_pt | float | yes | Mode Choice Model |
| mod_motbike | float | yes | Mode Choice Model |


### route_departure_model_output

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | My-Trac Companion |
| mytrac_is_valid | boolean | yes | My-Trac Companion |
| mytrac_last_modified | timestamp | yes | My-Trac Companion |
| choice_id | string | yes | My-Trac Companion |
| trip_dur_earlier | float | yes | My-Trac Companion |       
| trip_dur_later | float | yes | My-Trac Companion |                    
| trip_dur_ontime | float | yes | My-Trac Companion |                       
| trip_freq_earlier | int | yes | My-Trac Companion |                      
| trip_freq_later | int | yes | My-Trac Companion |                         
| trip_freq_ontime | int | yes | My-Trac Companion |                        
| trip_discount_earlier | float | yes | My-Trac Companion |          
| trip_discount_ontime | float | yes | My-Trac Companion |         
| trip_discount_later | float | yes | My-Trac Companion |            
| trip_walk_earlier | float | yes | My-Trac Companion |                      
| trip_walk_later | float | yes | My-Trac Companion |                          
| trip_walk_ontime | float | yes | My-Trac Companion |
| tod_earlier | float | yes | Time of Departure Model |
| tod_ontime | float | yes | Time of Departure Model |
| tod_later | float | yes | Time of Departure Model |


### shape

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | operators portal |
| mytrac_is_valid | boolean | yes | operators portal |
| mytrac_last_modified | timestamp | yes | operators portal |
| shape_id | string | yes | operators portal/gtfs |
| shape_pt_lat | double | yes | operators portal/gtfs |
| shape_pt_lon | double | yes | operators portal/gtfs |
| shape_pt_sequence | int | yes | operators portal/gtfs |
| shape_pt_sequence | int | yes | operators portal/gtfs |
| shape_dist_traveled | float | no | operators portal/gtfs |

### stop_time

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | operators portal |
| mytrac_is_valid | boolean | yes | operators portal |
| mytrac_last_modified | timestamp | yes | operators portal |
| trip_id | string | yes | operators portal/gtfs |
| arrival_time | time | conditional | operators portal/gtfs |
| departure_time | time | conditional | operators portal/gtfs |
| stop_id | string | yes | operators portal/gtfs |
| stop_sequence | int | yes | operators portal/gtfs |
| stop_headsign | string | no | operators portal/gtfs |
| pickup_type | enum | no | operators portal/gtfs |
| drop_off_type | enum | no | operators portal/gtfs |
| shape_dist_traveled | float | no | operators portal/gtfs |
| time_point | enum | no | operators portal/gtfs |

### stop

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | operators portal |
| mytrac_is_valid | boolean | yes | operators portal |
| mytrac_last_modified | timestamp | yes | operators portal |
| stop_id | string | yes | operators portal/gtfs |
| stop_code | string | no | operators portal/gtfs |
| stop_name | string | conditional | operators portal/gtfs |
| stop_desc | string | no | operators portal/gtfs |
| stop_lat | double | conditional | operators portal/gtfs |
| stop_lon | double | conditional | operators portal/gtfs |
| zone_id | string | conditional | operators portal/gtfs |
| stop_url | string | no | operators portal/gtfs |
| location_type | enum | no | operators portal/gtfs |
| parent_station | string | conditional | operators portal/gtfs |
| stop_timezone | string | no | operators portal/gtfs |
| wheelchair_boarding | string | no | operators portal/gtfs |
| level_id | string | no | operators portal/gtfs |

### transfer

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | operators portal |
| mytrac_is_valid | boolean | yes | operators portal |
| mytrac_last_modified | timestamp | yes | operators portal |
| from_stop_id | string | yes | operators portal/gtfs |
| to_stop_id | string | yes | operators portal/gtfs |
| transfer_type | enum | yes | operators portal/gtfs |
| min_transfer_time | int | no | operators portal/gtfs |

### trip

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | operators portal |
| mytrac_is_valid | boolean | yes | operators portal |
| mytrac_last_modified | timestamp | yes | operators portal |
| route_id | string | yes | operators portal/gtfs |
| service_id | string | yes | operators portal/gtfs |
| trip_id | string | yes | operators portal/gtfs |
| trip_headsign | string | no | operators portal/gtfs |
| trip_short_name | string | no | operators portal/gtfs |
| direction_id | int | no | operators portal/gtfs |
| block_id | int | no | operators portal/gtfs |
| shape_id | string | no | operators portal/gtfs |
| wheelchair_accessible | int | no | operators portal/gtfs |
| bikes_allowed | int | no | operators portal/gtfs |

### user

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | MyTrac-Companion  |
| mytrac_is_valid | boolean | yes | MyTrac-Companion  |
| mytrac_last_modified | timestamp | yes | MyTrac-Companion  |
| user_id | string | yes | MyTrac-Companion |
| user_registration_date | timestamp | yes | MyTrac-Companion |
| user_birthday | date | yes | MyTrac-Companion |
| user_impairment | enum | yes | MyTrac-Companion |
| user_gender | enum | yes | MyTrac-Companion |
| user_country | string | yes | MyTrac-Companion |
| user_nationality | enum | yes | MyTrac-Companion |
| user_occupation | enum | yes | MyTrac-Companion |
| user_reliability | enum | yes | MyTrac-Companion |
| user_imp_arr | enum | yes | MyTrac-Companion |
| user_tolerance | enum | yes | MyTrac-Companion |
| user_income | enum | yes | MyTrac-Companion |
| user_marital_status | enum | yes | MyTrac-Companion |
| user_tweets | int | yes | MyTrac-Companion |
| user_traveller_type | enum | yes | MyTrac-Companion |
| user_working_hours | int | yes | MyTrac-Companion |
| user_household | int | yes | MyTrac-Companion |
| user_car_avail | boolean | yes | MyTrac-Companion |
| user_moto_avail | boolean | yes | MyTrac-Companion |
| user_bike_avail | boolean | yes | MyTrac-Companion |
| user_interest_work | float | yes | MyTrac-Companion |
| user_interest_education | float | yes | MyTrac-Companion |
| user_interest_health | float | yes | MyTrac-Companion |
| user_interest_service | float | yes | MyTrac-Companion |
| user_interest_religion | float | yes | MyTrac-Companion |
| user_interest_history | float | yes | MyTrac-Companion |
| user_interest_hobby | float | yes | MyTrac-Companion |
| user_interest_eating | float | yes | MyTrac-Companion |
| user_interest_shopping | float | yes | MyTrac-Companion |
| user_comfort_pt | float | yes | MyTrac-Companion |
| user_comfort_car | float | yes | MyTrac-Companion |
| user_comfort_bike | float | yes | MyTrac-Companion |
| user_comfort_moto | float | yes | MyTrac-Companion |
| user_often_car | enum | yes | MyTrac-Companion |
| user_often_pt | enum | yes | MyTrac-Companion |
| user_arrive_ontime | enum | yes | MyTrac-Companion |
| user_lifestyle | enum | yes | MyTrac-Companion |
| user_reputation | double | yes | MyTrac-Companion |


user_impairment enum can have the following values:
* 1: Visual impairment
* 2: Other impairment
* 3: No impairment

user_gender enum can have the following values:
* 0: male
* 1: female
* 2: other

user_nationality enum can have the following values:
* 1: Dutch
* 2: Hellenic
* 3: Portuguese
* 4: Spanish
* 5: Other

user_occupation enum can have the following values:
* 1:Private employee
* 2:Public servant
* 3:Self-employed
* 4:Student
* 5:Retired
* 6:Unemployed

user_tolerance enum can have the following values:
* 1:Not tolerant at all
* 2:Intolerant
* 3:Neutral
* 4:Tolerant
* 5:Very tolerant

user_reliability enum can have the following values:
* 1:Not reliable at all
* 2:Unreliable
* 3:Neutral
* 4:Reliable
* 5:Extremely reliable

user_imp_arr enum can have the following values:
* 1:Not important at all
* 2:Somewhat important
* 3:Very important

user_income enum can have the following values:
* 1:Low
* 2:Medium
* 3:High

user_marital_status enum can have the following values:
* 0: single
* 1: married

user_traveller_type enum can have the following values:
* 0: Work / Education
* 1: Other

user_often_car enum can have the following values:
* 1: Never
* 2: Rarely
* 3: One/Two Times per week
* 4: Daily

user_often_pt enum can have the following values:
* 1: Never
* 2: Rarely
* 3: One/Two Times per week
* 4: Daily

user_arrive_ontime enum can have the following values:
* 1: Not important at all 
* 2: Somewhat important 
* 3: Very important 

user_lifestyle enum can have the following values:
* 1: Active - outdoor, sports-oriented, adventurous
* 2: Classy - elegant, luxurious, trendy
* 3: Domesticated - family-based, homely
* 4: Fun - pleasure seeking, sociable
* 5: Other

** User working hours need to be clarified **

### user_chooses_route

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | MyTrac-Companion  |
| mytrac_is_valid | boolean | yes | MyTrac-Companion  |
| mytrac_last_modified | timestamp | yes | MyTrac-Companion  |
| choice_id | string | yes | MyTrac-Companion |
| next_id | string | yes | MyTrac-Companion |
| user_id | string | yes | MyTrac-Companion |
| group_id| string | no | MyTrac-Companion |
| from_name | string | yes | MyTrac-Companion |
| from_address | string | yes | MyTrac-Companion |
| from_lon | double | yes | MyTrac-Companion |
| from_lat | double | yes | MyTrac-Companion |
| to_name | string | yes | MyTrac-Companion |
| to_lon | double | yes | MyTrac-Companion |
| to_lat | double | yes | MyTrac-Companion |
| to_address | string | yes | MyTrac-Companion |
| time | timestamp | yes | MyTrac-Companion | 
| mode | enum | no |  MyTrac-Companion |
| max_walk_distance | int | no |  MyTrac-Companion |
| num_itineraries | int | no | MyTrac-Companion |
| max_transfers | int | no | MyTrac-Companion |
| user_choice | int | yes | MyTrac-Companion |
| request_reply | json | yes | MyTrac-Companion |
| prediction_reply | json | yes | MyTrac-Companion |

choice_id is the unique identifier of this choice, which can be used to reference this choice from other items

next_id is the id of another choice in the same  "choice" session. This is to represent cases where the user is presented with choices from multiple OTP queries. 

To represent a user ignoring all the results returned for a request_reply, user_choice must be -1. 

mode can have the following values:
* 1: car
* 2: pt
* 3: bike/moto


### user_email

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | MyTrac-Companion  |
| mytrac_is_valid | boolean | yes | MyTrac-Companion  |
| mytrac_last_modified | timestamp | yes | MyTrac-Companion  |
| user_id | string | yes | MyTrac-Companion |
| email | string | yes | MyTrac-Companion |


### user_evaluates_activity

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | MyTrac-Companion  |
| mytrac_is_valid | boolean | yes | MyTrac-Companion  |
| mytrac_last_modified | timestamp | yes | MyTrac-Companion  |
| user_id | string | yes | MyTrac-Companion |
| activity_id | string | yes | MyTrac-Companion |
| rating | int | yes | MyTrac-Companion |
| time | timestamp | yes | MyTrac-Companion |

### user_evaluates_route

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | MyTrac-Companion  |
| mytrac_is_valid | boolean | yes | MyTrac-Companion  |
| mytrac_last_modified | timestamp | yes | MyTrac-Companion  |
| user_id | string | yes | MyTrac-Companion |
| choice_id | string | yes | MyTrac-Companion |
| happiness | int | yes | MyTrac-Companion |
| time | timestamp | yes | MyTrac-Companion |

happiness can have the following values:
* 1: very unhappy 
* 2: unhappy
* 3: neutral 
* 4: happy
* 5: very happy

### user_joins_group

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | MyTrac-Companion  |
| mytrac_is_valid | boolean | yes | MyTrac-Companion  |
| mytrac_last_modified | timestamp | yes | MyTrac-Companion  |
| user_id | string | yes | MyTrac-Companion |
| group_id | string | yes | MyTrac-Companion |
| time | timestamp | yes | MyTrac-Companion |

### user_purchases_ticket

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | MyTrac-Companion  |
| mytrac_is_valid | boolean | yes | MyTrac-Companion  |
| mytrac_last_modified | timestamp | yes | MyTrac-Companion  |
| user_id | string | yes | MyTrac-Companion |
| tickets_purchased | int | yes | MyTrac-Companion |
| time | timestamp | yes | MyTrac-Companion |

### user_reward

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | MyTrac-Companion  |
| mytrac_is_valid | boolean | yes | MyTrac-Companion  |
| mytrac_last_modified | timestamp | yes | MyTrac-Companion  |
| user_id | string | yes | MyTrac-Companion |
| is_login | boolean | yes | MyTrac-Companion |
| is_trip | boolean | yes | MyTrac-Companion |
| is_place | boolean | yes | MyTrac-Companion |
| is_show_poi | boolean | yes | MyTrac-Companion |
| is_rating_poi | boolean | yes | MyTrac-Companion |
| is_signup | boolean | yes | MyTrac-Companion |
| last_reward_done | timestamp | yes | MyTrac-Companion |

### user_twitter_account

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | MyTrac-Companion  |
| mytrac_is_valid | boolean | yes | MyTrac-Companion  |
| mytrac_last_modified | timestamp | yes | MyTrac-Companion  |
| user_id | string | yes | MyTrac-Companion |
| twitter_account | string | yes | MyTrac-Companion |

### user_uses_app

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | MyTrac-Companion  |
| mytrac_is_valid | boolean | yes | MyTrac-Companion  |
| mytrac_last_modified | timestamp | yes | MyTrac-Companion  |
| user_id | string | yes | MyTrac-Companion |
| time | timestamp | yes | MyTrac-Companion |

### user_views_activity

| Field Name | Field Type | Required | Source |
| ---------- | ---------- | -------- | ------ |
| mytrac_id | long | yes | MyTrac-Companion  |
| mytrac_is_valid | boolean | yes | MyTrac-Companion  |
| mytrac_last_modified | timestamp | yes | MyTrac-Companion  |
| user_id | string | yes | MyTrac-Companion |
| activity_id | string | yes | MyTrac-Companion |
| time | timestamp | yes | MyTrac-Companion |

