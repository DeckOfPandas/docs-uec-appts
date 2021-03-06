---
title: ABUS.10 Display Available Slots From a Specific Service
sidebar: usecase_sidebar
permalink: usep_abus10.html
---
{% include note-notpublished.html %}

## ABUS.10 Display Available Slots From a Specific Service
**_In order_** to book a patient into the selected provider service 

**_As a_** 111 Call Handler or urgent care service provider 

**_I want_** to view the available slots for a provider service for a specified timeframe.

### Commentary 
Where GP practices are huge joint practices or collections of federated practices, the list returned must be limited to only appointment slots at locations that fulfill the location requirement of the patient. This will nearly always be one location only. This may also be true for other urgent care providers either now or in the future.

GP Connect use case can be found at <a href="https://nhsconnect.github.io/gpconnect/appointments_use_case_search_for_free_slots.html" target=_blank>GP Connect search for free slots use case</a>

Providers may wish to demand-manage their slot collections.  GP practices may wish to have some appts available for urgent cases, and urgent care providers. 

From a 111 provider:
>_Some providers may have multiple diaries set up where clinics are being delivered by more than one clinician.
>Current proprietary solutions can offer up appointments grouped by diaries, forcing the 111 call handler to go through each diary looking for the best slot. In the national API, providers will be expected to return all the slots that match the start/end times, regardless of the provider's internal diary structure._ 

### Acceptance Criteria 
* The list **must** contain the actual geographic location of the appointment, rather than generic details of the location of the overall service provider. 
* The list **must** contain details of the start/end times of the available slots. 
* The list **must** contain details of the type of appt, such as face-to-face, video, telephone call-back. 
* The request **must** have a date/time window specified by the consumer system.  The start time will be taken as "now". It is expected that the end time of the window will be derived from the disposition of the patient (i.e. the "clinical need").
* The slots provided **must** be for a service that can respond to the current disposition of the patient. 
* The list **may** mark those appts that do not meet the current disposition timeframe, making them unbookable, if the user of the system does not have sufficient clinical authority to book appts outside the disposition timeframe. 
* The available appts **must** be capable of being retrieved from any provider, regardless of the relationship that the consuming user's organisation has with that provider. 
* The method of retrieval **must** not depend on any pre-installed data linkage processes between the requesting user's organisation and the provider organisation. 
* Where there are no available slots, the provider **must** send an appropriate response to indicate this. 
* The provider system **must** return available slots without requiring the potential patient to be "registered" with the provider. 
* This list **may** be capable of being quickly refreshed by the user or automatically as a timed event. 
* Where the provider has a number of diaries available to fulfil a request (say, when 2 or more clinicians are delivering surgeries at the same site) the provider must return all of those slots as part of the initial response. 
