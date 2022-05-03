# hurricane-analysis
hurricane analysis project from codecademy; using loops, lists, and dictionaries
# names of hurricanes
names = ['Cuba I', 'San Felipe II Okeechobee', 'Bahamas', 'Cuba II', 'CubaBrownsville', 'Tampico', 'Labor Day', 'New England', 'Carol', 'Janet', 'Carla', 'Hattie', 'Beulah', 'Camille', 'Edith', 'Anita', 'David', 'Allen', 'Gilbert', 'Hugo', 'Andrew', 'Mitch', 'Isabel', 'Ivan', 'Emily', 'Katrina', 'Rita', 'Wilma', 'Dean', 'Felix', 'Matthew', 'Irma', 'Maria', 'Michael']

# months of hurricanes
months = ['October', 'September', 'September', 'November', 'August', 'September', 'September', 'September', 'September', 'September', 'September', 'October', 'September', 'August', 'September', 'September', 'August', 'August', 'September', 'September', 'August', 'October', 'September', 'September', 'July', 'August', 'September', 'October', 'August', 'September', 'October', 'September', 'September', 'October']

# years of hurricanes
years = [1924, 1928, 1932, 1932, 1933, 1933, 1935, 1938, 1953, 1955, 1961, 1961, 1967, 1969, 1971, 1977, 1979, 1980, 1988, 1989, 1992, 1998, 2003, 2004, 2005, 2005, 2005, 2005, 2007, 2007, 2016, 2017, 2017, 2018]

# maximum sustained winds (mph) of hurricanes
max_sustained_winds = [165, 160, 160, 175, 160, 160, 185, 160, 160, 175, 175, 160, 160, 175, 160, 175, 175, 190, 185, 160, 175, 180, 165, 165, 160, 175, 180, 185, 175, 175, 165, 180, 175, 160]

# areas affected by each hurricane
areas_affected = [['Central America', 'Mexico', 'Cuba', 'Florida', 'The Bahamas'], ['Lesser Antilles', 'The Bahamas', 'United States East Coast', 'Atlantic Canada'], ['The Bahamas', 'Northeastern United States'], ['Lesser Antilles', 'Jamaica', 'Cayman Islands', 'Cuba', 'The Bahamas', 'Bermuda'], ['The Bahamas', 'Cuba', 'Florida', 'Texas', 'Tamaulipas'], ['Jamaica', 'Yucatn Peninsula'], ['The Bahamas', 'Florida', 'Georgia', 'The Carolinas', 'Virginia'], ['Southeastern United States', 'Northeastern United States', 'Southwestern Quebec'], ['Bermuda', 'New England', 'Atlantic Canada'], ['Lesser Antilles', 'Central America'], ['Texas', 'Louisiana', 'Midwestern United States'], ['Central America'], ['The Caribbean', 'Mexico', 'Texas'], ['Cuba', 'United States Gulf Coast'], ['The Caribbean', 'Central America', 'Mexico', 'United States Gulf Coast'], ['Mexico'], ['The Caribbean', 'United States East coast'], ['The Caribbean', 'Yucatn Peninsula', 'Mexico', 'South Texas'], ['Jamaica', 'Venezuela', 'Central America', 'Hispaniola', 'Mexico'], ['The Caribbean', 'United States East Coast'], ['The Bahamas', 'Florida', 'United States Gulf Coast'], ['Central America', 'Yucatn Peninsula', 'South Florida'], ['Greater Antilles', 'Bahamas', 'Eastern United States', 'Ontario'], ['The Caribbean', 'Venezuela', 'United States Gulf Coast'], ['Windward Islands', 'Jamaica', 'Mexico', 'Texas'], ['Bahamas', 'United States Gulf Coast'], ['Cuba', 'United States Gulf Coast'], ['Greater Antilles', 'Central America', 'Florida'], ['The Caribbean', 'Central America'], ['Nicaragua', 'Honduras'], ['Antilles', 'Venezuela', 'Colombia', 'United States East Coast', 'Atlantic Canada'], ['Cape Verde', 'The Caribbean', 'British Virgin Islands', 'U.S. Virgin Islands', 'Cuba', 'Florida'], ['Lesser Antilles', 'Virgin Islands', 'Puerto Rico', 'Dominican Republic', 'Turks and Caicos Islands'], ['Central America', 'United States Gulf Coast (especially Florida Panhandle)']]

# damages (USD($)) of hurricanes
damages = ['Damages not recorded', '100M', 'Damages not recorded', '40M', '27.9M', '5M', 'Damages not recorded', '306M', '2M', '65.8M', '326M', '60.3M', '208M', '1.42B', '25.4M', 'Damages not recorded', '1.54B', '1.24B', '7.1B', '10B', '26.5B', '6.2B', '5.37B', '23.3B', '1.01B', '125B', '12B', '29.4B', '1.76B', '720M', '15.1B', '64.8B', '91.6B', '25.1B']

# deaths for each hurricane
deaths = [90,4000,16,3103,179,184,408,682,5,1023,43,319,688,259,37,11,2068,269,318,107,65,19325,51,124,17,1836,125,87,45,133,603,138,3057,74]

# write your update damages function here:
def update_damages(damages):
    updated_damages_list = []
    conversion = {"M":1000000,"B":1000000000}
    for amount in damages:
        if amount == 'Damages not recorded':
            updated_damages_list.append(amount)
        if amount[-1] =="M":
            new_amount = float(amount[:-1]) *conversion["M"]
            updated_damages_list.append(new_amount)
        if amount[-1] =="B":
            new_amount = float(amount[:-1]) *conversion["B"]
            updated_damages_list.append(new_amount)
    return updated_damages_list
damages = update_damages(damages)






# write your construct hurricane dictionary function here:
def construct_hurricane_dictionary(names,months,years,max_sustained_winds,areas_affected,deaths):
    hurricane_dictionary = {}
    for i in range(len(names)):
        hurricane_dictionary.update({names[i]:{"Name":names[i],"Month":months[i],"Year":years[i],"Max Sustained Wind":max_sustained_winds[i],"Areas Affected":areas_affected[i],"Damages":damages[i],"Deaths":deaths[i]}})
    return hurricane_dictionary
hurricane_dictionary = construct_hurricane_dictionary(names,months,years,max_sustained_winds,areas_affected,deaths)
# print(hurricane_dictionary)




# write your construct hurricane by year dictionary function here:

def construct_hurricane_by_year(hurricanes):
    hur_by_year = {}
    for i in hurricanes:
        year = hurricanes[i]["Year"]
        name = hurricanes[i]
        if year not in hur_by_year:
            hur_by_year[year] = [name]
        else:
            hur_by_year[year].append(name)
    return hur_by_year
hur_by_year = construct_hurricane_by_year(hurricane_dictionary)





# write your count affected areas function here:

def count_affected_areas(hurricane):
    count_affected = {}
    for value in hurricane.values():
        for i in value["Areas Affected"]:
            if i not in count_affected:
                count_affected[i] = 1
            else:
                count_affected[i] +=1
    return count_affected
# print(count_affected_areas(hurricane_dictionary))

affected_areas = count_affected_areas(hurricane_dictionary)



# write your find most affected area function here:

def count_affected_areas(affected_areas):
    max_affected_area = "Central America"
    max_affected_count = affected_areas[max_affected_area]
    for key in affected_areas:
        if affected_areas[key]>max_affected_count:
            max_affected_area = key
        else:
            continue
    return {max_affected_area:max_affected_count}
# print(count_affected_areas(affected_areas))



# write your greatest number of deaths function here:

def num_deaths(hurricanes):
    death_count = {}
    for key, value in hurricanes.items():
        death_count.update({key:value["Deaths"]})

    max_death_cane = "Cuba I"
    max_death_count = 0
    for key in death_count:
        if death_count[key]>max_death_count:
            max_death_cane = key
            max_death_count = death_count[key]
    return {max_death_cane:max_death_count}

# print(num_deaths(hurricane_dictionary))
max_deaths = num_deaths(hurricane_dictionary)




# write your catgeorize by mortality function here:

def mortality_category(hurricanes):
    death_count = {}
    for key, value in hurricanes.items():
        death_count.update({key:value["Deaths"]})
    mortality_scale = {0: 0,
                   1: 100,
                   2: 500,
                   3: 1000,
                   4: 10000}
    # return death_count
    hurricanes_by_mortality = {0:[],1:[],2:[],3:[],4:[],5:[]}
    for key,value in death_count.items():
        if death_count[key] <=0:
            hurricanes_by_mortality[0].append(key)
        elif death_count[key]<=100 and death_count[key]>0:
            hurricanes_by_mortality[1].append(key)
        elif death_count[key] <=500 and death_count[key]>100:
            hurricanes_by_mortality[2].append(key)
        elif death_count[key]<=1000 and death_count[key]>500:
            hurricanes_by_mortality[3].append(key)
        elif death_count[key]<=10000 and death_count[key]>1000:
            hurricanes_by_mortality[4].append(key)
        elif death_count[key]>10000:
            hurricanes_by_mortality[5].append(key)
    return hurricanes_by_mortality
mortality_categories = mortality_category(hurricane_dictionary)

print(mortality_categories)


# write your greatest damage function here:
def greatest_damage(hurricane_dictionary):
    max_damage_hurricane = ""
    max_damage = 0
    for key,value in hurricane_dictionary.items():
        try:
            if value["Damages"] > max_damage:
                max_damage_hurricane = key
                max_damage = value["Damages"]
        except:
            continue
    max_damage_dict = {max_damage_hurricane:max_damage}
    return max_damage_dict
max_damage_hurricane = greatest_damage(hurricane_dictionary)
print(max_damage_hurricane)



# write your catgeorize by damage function here:
def categorize_damage(hurricane_dictionary):
    damage_category_dict= {0:[],1:[],2:[],3:[],4:[],5:[]}
    for key,value in hurricane_dictionary.items():
        try:
            if value["Damages"] <= 0:
                damage_category_dict[0].append(key)
            elif value["Damages"] > 0 and value["Damages"]<=100000000:
                damage_category_dict[1].append(key)
            elif value["Damages"] > 100000000 and value["Damages"]<=1000000000:
                damage_category_dict[2].append(key)
            elif value["Damages"] > 1000000000 and value["Damages"]<=10000000000:
                damage_category_dict[3].append(key)
            elif value["Damages"] > 10000000000 and value["Damages"]<=50000000000:
                damage_category_dict[4].append(key)
            elif value["Damages"]>50000000000:
                damage_category_dict[5].append(key)
        except:
            continue
    return damage_category_dict

damage_categories = categorize_damage(hurricane_dictionary)
print(damage_categories)
