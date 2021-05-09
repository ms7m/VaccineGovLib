# VaccineGov 
> A python library that wraps around the https://vaccines.gov website..

***

### Quickstart

***Install***
```bash

# pip
pip install vaccinegov 

# poetry
poetry add vaccinegov

```

***Initialize***
```python
>>> import vaccinegov
>>>
>>> api = vaccinegov.VaccinesGov()
```
***

***Get Vaccines***
```python
>>> vaccines = api.available_vaccines()
>>> vaccines
[<VaccineManufacturer ModernaCOVIDVaccine>, <VaccineManufacturer Pfizer-BioNTechCOVIDVaccine>, <VaccineManufacturer JohnsonJohnsonsJanssenCOVIDVaccine>]
>>>
>>> vaccines[0].name
'Moderna COVID Vaccine'
>>>
```
> This will show all vaccines available to the U.S Population

***

***Searching via Coordinates***
```python

>>> providers = api.search_via_coordinates(
...     vaccines=vaccines,
...     latitude=40.765714,
...     longitude=-73.9856
... )
>>> providers
[   <VaccineProvider 86f2d4ed-2176-4f3c-84e9-ec9de36b3511>,
    <VaccineProvider 7abceabe-65a1-4ca1-90b6-3d18a6369bdb>,
    ...
]
>>> providers[0].name
'Walgreens Co. #14297'
```

***

***Searching via Zip Code***
```python

>>> providers = api.search_via_zip_code(vaccines=vaccines, zipcode=10019)
>>> providers
[   <VaccineProvider 86f2d4ed-2176-4f3c-84e9-ec9de36b3511>,
    <VaccineProvider 7abceabe-65a1-4ca1-90b6-3d18a6369bdb>,
    ...
]
>>> providers[0].name
'Walgreens Co. #14297'
```
***

***View provider metadata***
```python
>>> selected_provider = providers[0]
>>> 
>>> selected_provider.name
'Walgreens Co. #14297'

>>> selected_provider.phone
'212-582-3463'

>>> selected_provider.location.addresses
['900 8th Ave', '']

>>> selected_provider.location.city
'New York'

>>> selected_provider.prescreening_site
'https://www.walgreens.com/findcare/vaccination/covid-19'

>>> selected_provider.vaccines_available
[<VaccineManufacturer Pfizer-BioNTechCOVIDVaccine>]

>>> selected_provider.vaccines_offered
[<VaccineManufacturer ModernaCOVIDVaccine>, <VaccineManufacturer Pfizer-BioNTechCOVIDVaccine>, <VaccineManufacturer JohnsonJohnsonsJanssenCOVIDVaccine>]
>>> 
```
### ⚠️ Warning
Since this is techincally a U.S Government website, using this library may violate the warning notice.
> Unauthorized access to or unauthorized use of U.S. Government information or information systems is subject to criminal, civil, administrative, or other lawful action;

### Development
**Contributing**
- Use poetry
- Black before committing.
- Run tests
- Open PR to ``dev`` branch.