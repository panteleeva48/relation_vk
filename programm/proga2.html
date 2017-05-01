
# coding: utf-8

# In[1]:

import urllib.request
import json
import re
import matplotlib.pyplot as plt
from matplotlib import style
from datetime import datetime, date, time


# In[2]:

def writefile(namefile,result):
    file = open(namefile, "w", encoding = "utf-8")
    file.write(result)
    file.close()


# In[3]:

def file(name):
    f = open(name, 'r', encoding = 'utf-8')
    fr = f.read()
    f.close()
    return fr


# In[4]:

def clean1(string):
    regTag = re.compile('<.*?>', flags=re.U | re.DOTALL)
    clean_t = regTag.sub(' ', string)
    clean_t = re.sub('-&gt;','->',clean_t)
    return clean_t


# In[5]:

def clean2(string):
    clean_t = re.sub(r'Телефон',r'Телефон ',string)
    clean_t = re.sub(r'(\([0-9]{3}\)) ',r'\1',clean_t)
    clean_t = re.sub(r' (\([0-9]{3}\))',r'\1',clean_t)
    clean_t = re.sub(r' (\([0-9]{3}\)) ',r'\1',clean_t)
    clean_t = re.sub('\[.*?\|(.*?)\]',r'\1',clean_t)
    emoji_pattern = re.compile("["
        u"\U0001F600-\U0001F64F"  # emoticons
        u"\U0001F300-\U0001F5FF"  # symbols & pictographs
        u"\U0001F680-\U0001F6FF"  # transport & map symbols
        u"\U0001F1E0-\U0001F1FF"  # flags (iOS)
                           "]+", flags=re.UNICODE)
    clean_t = emoji_pattern.sub(r'', clean_t)
    clean_t = re.sub('\\u2728', '', clean_t)
    clean_t = re.sub('#',' ',clean_t)
    return clean_t


# In[6]:

def posts():
    ids = []
    texts = []
    for k in range (2):
        #print(k)
        if k == 0:
            offset_num = str(0)
        else:
            offset_num = str(k) + '00'
        req = urllib.request.Request('https://api.vk.com/method/wall.get?owner_id=-64607113&count=100&offset='+offset_num)
        response = urllib.request.urlopen(req)
        result = response.read().decode('utf-8')
        data = json.loads(result)
        #print(data)
        for i in range (1,101):
            #print(i)
            if data["response"][i]["post_type"] == "post":
                text = data["response"][i]["text"]
            if data["response"][i]["post_type"] == "copy":
                if not "copy_text" in data["response"][i]:
                    text = ""
                else:
                    text = data["response"][i]["copy_text"]
            post_id = data["response"][i]["id"]
            texts.append(text)
            ids.append(post_id)
            #print(text, post_id)
    return ids, texts


# In[7]:

def dictpost():
    ids, texts = posts()
    d = dict(zip(ids, texts))
    return d


# In[8]:

def filepost():#функция скачивающая посты в файл
    dictposts = dictpost()
    comm = ''
    for num_id in dictposts:
        string = clean1(dictposts[num_id])
        if comm == '':
            comm = string
        else:
            comm = comm + '\n' + string
    #print(comm)
    writefile('posts.txt',comm)


# In[9]:

filepost()#posts.txt - файл с постами


# In[10]:

def comments():
    comms = {}
    ids, texts = posts()
    ids_user = {}
    for id_num in ids:
        comm_uni = []
        users = []
        #print(id_num)
        for k in range (2):
            #print(k)
            if k == 0:
                offset_num = str(0)
            else:
                offset_num = str(k) + '00'
            req = urllib.request.Request('https://api.vk.com/method/wall.getComments?owner_id=-64607113'+'&post_id='+str(id_num)+'&count=100&offset='+offset_num)
            response = urllib.request.urlopen(req)
            result = response.read().decode('utf-8')
            #print(result)
            data = json.loads(result)
            i = 1
            while i < len(data["response"]):
                #print(i)
                if not "text" in data["response"][i]:
                    comm = ''
                    id_user = ''
                else:
                    comm = data["response"][i]["text"]
                    id_user = data["response"][i]["from_id"]
                comm_uni.append(comm)
                users.append(id_user)
                i += 1
        #print(comm_uni)
        comms[id_num] = comm_uni
        ids_user[id_num] = users
    comms = json.dumps(comms, ensure_ascii=False)
    ids_user = json.dumps(ids_user, ensure_ascii=False)
    return comms, ids_user


# In[11]:

comms, ids_user = comments()
writefile('comms.txt',str(comms))#словарь: ключи - id постов, значения - комментарии к ним
writefile('ids_user.txt',str(ids_user))#словарь: ключи - id постов, значения - id userа, написавшего комментарий


# In[12]:

def filecomments():
    dictcomms = file('comms.txt')
    dictcomms = json.loads(dictcomms)   
    final = ''
    for num_id in dictcomms:
        allcomm = ''
        #print(type(dictcomms))
        for every in dictcomms[num_id]:
            #print(dictcomms[num_id])
            string = clean1(every)
            if allcomm == '':
                allcomm = string
            else:
                allcomm = allcomm + '\n' + string
        if final == '':
            final = str(num_id) + '\n' +allcomm
        else:
            final = final + '\n\n\n\n' + str(num_id) + '\n' + allcomm
    writefile('comments.txt',final)


# In[13]:

filecomments()


# In[14]:

def number(string):
    g = clean1(string)
    g2 = clean2(g)
    #print(g2)
    strm = g2.split(' ')
    #print(strm)
    return strm


# In[15]:

def numpost():
    lengths = []
    dictposts = dictpost()#словарь: ключи - ids поста, значения - пост
    #print(dictposts)
    for num_id in dictposts:#каждый пост просматривает
        if dictposts[num_id] == '':# если ничего не написано в посту
            strm = []# тогда массив из 0 элементов
        else:# если что-то написано
            strm_0 = number(dictposts[num_id])#разделяет на слова
            #print(strm_0)
            strm = []
            for x in strm_0:# чтобы не было пустых строк
                x = x.strip(' .,()[];:?!«»{}-/')
                if x.startswith('http'):
                    x = ''
                if x != '':
                    strm.append(x)#добавляет в массив непустые слова
            #print(strm)
        length = len(strm)
        lengths.append(length)
    #print(lengths)
    return lengths


# In[16]:

numpost()


# In[17]:

def numcomm():
    lengths = []
    dictcomms = json.loads(file('comms.txt'))
    av = []
    num_us = {}
    for num_id in dictcomms:
        numb = []
        if dictcomms[num_id] == []:
            numb = []
        else:
            for p in dictcomms[num_id]:
                if p == '':
                    strm = []
                else:
                    strm_0 = number(p)
                    strm = []
                    for x in strm_0:
                        x = x.strip(' .,()[];:?!«»{}-/')
                        if x.startswith('http'):
                            x = ''
                        if x != '':
                            strm.append(x)
                length = len(strm)
                numb.append(length)
            num_us[num_id] = numb
            #print (numb)
        summ = 0
        for y in numb:
            summ = summ + y
        if summ == 0:
            average = 0
        else:
            average = round(summ / len(numb))
        av.append(average)
    #print(av)
    return av, num_us


# In[18]:

av, num_us = numcomm()
av = json.dumps(av, ensure_ascii=False)#массив из средних длин комментарие к каждому посту
num_us = json.dumps(num_us, ensure_ascii=False)#словарь: ключ - id поста, значение - массив из длин комментарие к этому посту
writefile('num_us.txt',str(num_us))


# In[19]:

def graph1():
    av, num_us = numcomm()
    post = numpost()
    dictlen = dict(zip(post, av))
    #print(dictlen)
    x = []
    y = []
    for key in sorted(dictlen):
        x.append(key)
        y.append(dictlen[key])
    #print(x)
    #print(y)
    style.use('ggplot')
    plt.plot(x, y, 'purple')
    plt.title('Зависимость длины комментария от длины поста')
    plt.ylabel('Средняя длина комментариев')
    plt.xlabel('Длина поста')
    plt.savefig('relation.png')
    plt.show()
    plt.close()


# In[20]:

graph1()


# In[21]:

def people():
    ids_user = json.loads(file('ids_user.txt'))
    num_us = json.loads(file('num_us.txt'))
    mass1 = []# id чувака
    mass2 = []# длина его комментария
    for x in ids_user:
        for i in ids_user[x]:
            mass1.append(i)
    for y in num_us:
        for h in num_us[y]:
            mass2.append(h)
    return mass1, mass2


# In[22]:

mass1, mass2 = people()
#print(mass1)
#print(mass2)
#print(len(mass1))
#print(len(mass2))
mass1 = json.dumps(mass1, ensure_ascii=False)
mass2 = json.dumps(mass2, ensure_ascii=False)
writefile('id_people.txt',str(mass1))#id userа, который написал коммент
writefile('length.txt',str(mass2))#длина его комментария


# In[23]:

def calculate_age(born):
    today = date.today()
    try: 
        birthday = born.replace(year=today.year)
    except ValueError:
        birthday = born.replace(year=today.year, day=born.day-1)
    if birthday > today:
        return today.year - born.year - 1
    else:
        return today.year - born.year


# In[24]:

def what_city(id_city):
    req = urllib.request.Request('https://api.vk.com/method/database.getCitiesById?city_ids='+str(id_city))
    response = urllib.request.urlopen(req)
    result = response.read().decode('utf-8')
    data = json.loads(result)
    city = data["response"][0]['name']
    return city


# In[25]:

def id_people():
    mass1 = file('id_people.txt')
    data = json.loads(mass1)
    return(data)# делает массив из id людей, которые написали комментарии


# In[26]:

def user_know(id_us):
    req = urllib.request.Request('https://api.vk.com/method/users.get?user_ids=' + str(id_us) + '&fields=bdate,city')
    response = urllib.request.urlopen(req)
    result = response.read().decode('utf-8')
    data = json.loads(result)
    return data


# In[27]:

def info():
    mass = id_people()
    inf = []
    #k = 1
    for i in mass:
        #print(i)
        #print(str(k) + '--' + str(i))
        data = user_know(i)
        inf.append(data["response"][0])
        #k += 1
        #if k == 2000:
        #    break
    #print(inf)
    inf = json.dumps(inf, ensure_ascii=False)
    writefile('inf.txt',str(inf))


# In[28]:

info()


# In[29]:

def ages_cities():
    inf = file('inf.txt')
    data = json.loads(inf)
    ages = []
    cities = []
    for x in data:
        #print(x)
        if 'bdate' in x:
            birth = x['bdate']
            if len(birth) > 5: # проверяю, правильно ли записана дата
                day, month, year = [int(x) for x in birth.split(".")]
                born = date(year, month, day)
                age = calculate_age(born)
            else:
                age = 0
        else:# это муссор: 0 обозначаю тех, кого не указан год рождения(только день и месяц) или вообще ничего не указано
            age = 0#noage
        ages.append(age)# int
        if 'city' in x:
            city = x['city']
        else:
            city = 0
        cities.append(city)
    return ages, cities


# In[30]:

ages, cities = ages_cities()
print(ages)
print(cities)


# In[31]:

def allinfo():
    all_inf = {}
    ages, cities = ages_cities()
    id_man = file('id_people.txt')
    id_man = json.loads(id_man)
    lengths = file('length.txt')
    lengths = json.loads(lengths)
    i = 0
    #id_man = id_man[:1999:]#! УДАЛИТЬ!!!!!
    #lengths = lengths[:1999:]#! УДАЛИТЬ!!!!!
    print(len(id_man),len(lengths),len(ages),len(cities))
    #print(id_man)
    #print(lengths)
    #print(ages)
    #print(cities)
    for one in id_man:
        all_inf[i] = [id_man[i],lengths[i],ages[i], cities[i]]
        i += 1
    #print(all_inf)    
    return all_inf


# In[32]:

all_inf = allinfo()
all_inf = json.dumps(all_inf, ensure_ascii=False)
writefile('all_inf.txt',str(all_inf))# собираю всю инфу про users


# In[33]:

def aver(lst):
    s = 0
    for i in lst:
        s += i
    return round(s / len(lst))


# In[34]:

def graf_age():
    all_inf = file('all_inf.txt')
    all_inf = json.loads(all_inf)
    dict_age = {}# словарь: ключи - возраст, значения массив из длин комментариев
    for p in all_inf:
        #print(all_inf[p])
        if all_inf[p][2] not in dict_age:
            dict_age[all_inf[p][2]] = [all_inf[p][1]]
        else:
            dict_age[all_inf[p][2]].append(all_inf[p][1])
    #print(dict_age)
    for z in dict_age:
        dict_age[z] = aver(dict_age[z])# средняя длина комментариев
    #print(dict_age)
    dict_age2 = {}
    for k in sorted(dict_age.keys()):# в порядке возрастание модифицирует dict_age
        if k != 0 and k < 100:
            dict_age2[k] = dict_age[k]
    #print(dict_age2)
    ages = []
    length = []
    for key in dict_age2:
        ages.append(key)
        length.append(dict_age2[key])
    print(ages,length)
    plt.bar(ages, length)
    plt.title('Зависимость длины комментария от возраста')
    plt.ylabel('Средняя длина комментариев')
    plt.xlabel('Возраст')
    plt.savefig('relation2.png')
    plt.show()
    plt.close()


# In[35]:

graf_age()


# In[36]:

def graf_city_age():
    all_inf = file('all_inf.txt')
    all_inf = json.loads(all_inf)
    dict_city_age = {}# словарь: ключи - id города, значение - () из длины и возраста
    for p in all_inf:
        #print(all_inf[p])
        if all_inf[p][3] not in dict_city_age:
            dict_city_age[all_inf[p][3]] = [(all_inf[p][1],all_inf[p][2])]
        else:
            dict_city_age[all_inf[p][3]].append((all_inf[p][1],all_inf[p][2]))
    #print(dict_city_age)
    for city in dict_city_age:
        diction = {}
        for h in dict_city_age[city]:
            if h[1] not in diction:#h[1] - возраст
                diction[h[1]] = [h[0]]
            else:
                diction[h[1]].append(h[0])
        #print(city, diction)
        for z in diction:
            diction[z] = aver(diction[z])
        #print(diction)
        dict_age2 = {}
        for k in sorted(diction.keys()):
            if k != 0 and k < 100:
                dict_age2[k] = diction[k]
        #print(dict_age2)
        ages = []
        length = []
        for key in dict_age2:
            ages.append(key)
            length.append(dict_age2[key])
        #print(ages)
        #print(length)
        print(city,ages,length)
        if city == 0:
            plt.bar(ages, length)
            plt.title('Другие города (пользователь скрыл информацию о городе)')
            plt.ylabel('Средняя длина комментариев')
            plt.xlabel('Возраст')
            plt.savefig('different_cities.png')
            plt.show()
            plt.close()
        else:
            if len(ages) == 0:
                continue
            else:
                city = what_city(city)
                plt.bar(ages, length)
                plt.title(str(city))
                plt.ylabel('Средняя длина комментариев')
                plt.xlabel('Возраст')
                plt.savefig(str(city) +'.png')
                plt.show()
                plt.close()


# In[37]:

graf_city_age()


# In[82]:

def all_city_len():# график 
    all_inf = file('all_inf.txt')
    all_inf = json.loads(all_inf)
    dict_city = {}# словарь: ключи - город, значения массив из длин комментариев
    for p in all_inf:
        if all_inf[p][3] not in dict_city:
            dict_city[all_inf[p][3]] = [all_inf[p][1]]
        else:
            dict_city[all_inf[p][3]].append(all_inf[p][1])
    for z in dict_city:
        dict_city[z] = aver(dict_city[z])# средняя длина комментариев
    #print(dict_city)
    cities = []
    for g in dict_city:
        if g == 0:
            cities.append('Неизвестно')
        else:
            cities.append(what_city(g))
    #print(cities)
    length = []
    for key in dict_city:
        length.append(dict_city[key])
    s = {}
    k = 0
    #print(length)
    #print(cities)
    for c in cities:
        s[cities[k]]=length[k]
        k += 1
    #print(s)
    s = json.dumps(s, ensure_ascii=False)
    writefile('city_len.txt',str(s))


# In[83]:

all_city_len()


# In[87]:

def grapf_cit():
    s = file('city_len.txt')
    s = json.loads(s)
    l = lambda x: x[1]
    sort_s = sorted(s.items(), key=l, reverse=True)
    sort_s = sort_s[:50:]#рисую города, у которых самые большие комментарии
    plt.bar(
        range(len(sort_s)), 
        [i[1] for i in sort_s]
            )
    plt.xticks(
        range(len(sort_s)), 
        [i[0] for i in sort_s], 
        rotation='vertical'
            )
    plt.title('Зависимость длины комментариев от города')
    plt.ylabel('Средняя длина комментариев')
    plt.xlabel('Город')
    plt.savefig('relation3.png')
    plt.show()
    plt.close()


# In[88]:

grapf_cit()


# In[ ]:



