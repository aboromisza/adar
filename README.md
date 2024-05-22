# adar
ideiglenes
enable secret "jelszó"
username vmi password valami
service password-encryption

ip domain-name 
crypto key generate rsa (1024)
ip ssh version 2
line consol 0
login local
 
line vty 0 15
login local
transport input ssh 
do wr
interface vlan 1 ip address
no shutdown
ip default-gateway  
banner motd " "
copy startup-config tftp:
interfacef0/1
ipv6 address 
ipv6 unicast-routing
ipv6 address  link-local
show running-config
vlsmcalc.com

f = open("demofile.txt", "w")
lista = ""
for i in range(1000):
    lista += str(i) + ";"
f.write(lista)

f.close()

#open and read the file after the appending:
f = open("demofile.txt", "r")
print(f.read())

with open("probaszamok.txt", "w") as kimenet:
    index = 0
    for i in lista:
        if index < len(lista)-1:
            kimenet.write(str(i) + ";")
            index += 1
        else:
            kimenet.write(str(i))
            

file = open("probaszamok.txt")
for i in file:
    seged = ','.join(i.strip().split(";"))
    
    alapszo = "zorglub"
print(fordito(alapszo))
print(alapszo[::-1])

tukorlista = []
for betu in alapszo:
  tukorlista.insert(0, betu)

print(''.join(tukorlista))


def fordito(szo):
  tlista=[]
  for betu in szo:
    tlista.insert(0, betu)
  print("".join(tlista))

szo = input('Írd be a tükrözni kívánt szót! : ')
fordito(szo)


# A beolvasott szöveget írasd ki szavanként külön sorba!'''

szoveg = 'A beolvasott szöveget írasd ki szavanként külön sorba!'
szoveg_lista = szoveg.split()
print('\n'.join(szoveg_lista))'''

# Olvasson be stringeket ”*” végjelig. Írja ki a leghosszabbat és a legnagyobbat!

ezek_sztringek = "Kávéfőző*Uborka*auto*Politikus*Rebarbara*csiga*elon musk"

def sztring_vizsgalo(x):
    hossz = 0
    leghosszabb = ''
    sz_lista = x.split('*')
    for szo in sz_lista:
        if hossz < len(szo):
            leghosszabb = szo
    print(f'A leghoszabb a(z) {leghosszabb} szó.')
    sz_lista.sort()
    print(f'A legnagyobb pedig a(z) {(sz_lista[0])} szó, bármit is jelentsen a "legnagyobb"')
3
sztring_vizsgalo(ezek_sztringek)


# Vowel eater – ”magánhangzó evő” – a beolvasott szöveget írd ki magánhangzók nélkül!

def hangzo_killer(szo):
    maganhangzok = 'a, á, e, é, i, í, o, ó, ö, ő, u, ú, ü, ű'  # azért nem lista eleve, mert így volt a wikin :)
    maganhangzok_lista = maganhangzok.split(', ')
    szo2 = ""
    for i in range(len(szo)):
        if szo[i] not in maganhangzok_lista:
            szo2 += szo[i]
    print(szo2)

hangzo_killer(input('Add meg a magánhangó-purgálni kívánt szót! '))


# Tölts fel egy listát 10 véletlenszámmal úgy, hogy ne legyenek ismétlődések benne!


szamlista =[]

while (len(szamlista)) != 10:
   szam = random.randint(1, 100)
   if szam not in szamlista:
       szamlista.append(szam)
print(szamlista)

composer create-project laravel/laravel
php artisan make:migration create_drinks_table 
php artisan make:model Drink --controller --resource --requests --migrat
ion
dbSeeder-ben a 'run' ban $this->call([StudentSeeder::class ]) -al majd futtatni
php artisan make:controller DrinkResourceController --resource --model=Drink
php artisan make:resource DrinkResource  
php artisan make:resource DrinkCollection
php artisan make:resource DrinkDetaledResource
php artisan install:api
php artisan make:model Category
php artisan make:controller CategoriesController --resource
php artisan db:seed
  
$table->foreignIdFor(\App\Models\Student::class)->constrained();


DrinkResource
public function toArray(Request $request): array
    {
        return ['id' =>$this-> id,
                'name' => $this-> name,
            'price' => ($this->discounted_price ==null ? $this->price : $this-> discounted_price),
            'discounted' =>($this->discounted_price != null)
        ];
    
DrinkCollection
public function toArray(Request $request): array
    {
        return ['data' => $this ->collection,
            'succes' => true,
           'message' =>""
    
       ];
    }

DrinkResourceController
public function index()
    {
        return new FlavorCollection(Flavor::all());
    }

api
Route::apiResource('drinks', \App\Http\Controllers\DrinkResourceController::class)
    ->only(['index', 'show', 'store']);

DrinkDetaledResource
public function toArray(Request $request): array
    {
        return [
            'data' => ['id' =>$this-> id,
                'name' => $this-> name,
            'ingredients' => '',
            'description' => $this->description,
            'quantity' => $this->quantity,
                'price' => $this->price,
                'discounted_price' => $this-> discounted_price,
                'flavor' => new FlavorResource(Flavor::find($this->flavor_id)),
            ],
            'succes' => true,
            'message' =>""
        ];
    }

drink (model)

class Drink extends Model
{
    use HasFactory;

    protected $guarded = [];

    public function ingredients() : HasMany
    {
        return $this->hasMany(Ingredient::class);
    }
}

masik flavResCont
"   public function store(Request $request)
    {
        $flavor = Flavor::create($request->all());
        return response()->json(['flavor' =>$flavor]);
    }"

<script setup>
import { http } from '@/utils/http';
import { reactive, onMounted, ref } from 'vue';
import { RouterLink } from 'vue-router';
const drinks = reactive([]);
async function getData(){
  const response = await http.get('drinks')
  for (const item of response.data.data){
    const obj ={
      'id': item.id,
      'name': item.name,
      'price': item.price,
      'discounted': discount(item.discounted)
    }
    drinks.push(obj)
  }
}
function discount(data){
  if (data === true){
    return "Akciós"
  }
  else{
    return "Nem akciós"
  }
}
onMounted(getData)
</script>

<template>
<main class="container">
  <h1>Italok</h1>
  <hr>
  <table class="table table-responsive">
    <thead>
      <tr>
        <th>Név</th>
        <th>Ár</th>
        <th>Akciós</th>
        <th>Művelet</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="drink in drinks" :key="drink.id">
        <td>{{ drink.name }}</td>
        <td>{{ drink.price }}</td>
        <td>{{ drink.discounted }}</td>
        <td><router-link class="btn btn-primary" :to="`/drinks/${drink.id}`">Megtejíntés</router-link></td>
      </tr>
    </tbody>
  </table>
</main>
</template>

import { createRouter, createWebHistory } from 'vue-router'
import HomeView from '../views/HomeView.vue'

const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: [
    {
      path: '/',
      name: 'home',
      component: HomeView,
      meta:{
        title: "Kezdőlap"
      }
    },
    {
      path: '/new',
      name: 'new',
      component: ()=> import("@/views/CreateNewDrinkFormView.vue"),
      meta:{
        title: 'Hozzáadás'
      }
    },
    {
      path: '/drinks/:id',
      name: 'drink',
      component: ()=> import("@/views/DrinkDataView.vue"),
      meta:{
        title: 'Adatok'
      }
    }
  ]
})
router.beforeEach((to,from, next)=>{
  document.title= `${to.meta.title}`;
  next();
})
export default router

<script>
import {http} from "@/utils/http.js"
import {RouterLink} from "vue-router"
export default{
    data(){
        return{
            drink: {},
            visible: false
        }
    },
    components:{
        RouterLink
    },
    methods:{
        async getData(){
            const response = await http.get(`drinks/${this.$route.params.id}`);
            this.drink = await response.data.data;
            this.visible = true;
        }
    },
    mounted(){
        this.getData();
    }
}
</script>

<template>
<main class="container" v-show="visible === true">
    <h1>{{ drink.name }}</h1>
    <hr>
    <ul class="list-group">
        <li class="list-group-item">
            Összetevök:
            <span v-for="ingredient in drink.ingredients"
            :key="ingredient.id" class="badge bg-secondary mx-1">{{ ingredient.name }}</span>
        </li>
        <li class="list-group-item">Leírás: {{ drink.description }}</li>
        <li class="list-group-item">Ár {{ drink.price }} Ft</li>
        <li class="list-group-item">Csökkentett ár: 
            <span v-if="drink.discounted_price === null">Nincs</span>
            <span v-else>{{drink.discounted_price}}</span>
        </li>
        <li class="list-group-item" v-if="drink.flavor">Ízetsítés: {{ drink.flavor.name }}</li>
        <li class="list-group-item"> 
            <router-link to="/" class="btn btn-danger">Vissza</router-link>
        </li>
    </ul>
</main>
</template>

<style scoped>

</style>

import axios from "axios";
const http = axios.create({
    baseURL: "http://127.0.0.1:8000/api/"
})
export {http}


<script setup>
import {Form as VForm, Field, ErrorMessage, FieldArray} from 'vee-validate';
import {onMounted, reactive, ref} from 'vue';
import {http} from '@/utils/http.js'
import * as yup from 'yup'
const ingredients = ref(['']);
const flavors = reactive([]);
async function getData(){
    const response = await http.get('flavors');
    for (const item of response.data.data){
        flavors.push(item)
    }
}
const addIngredient=()=>{
    ingredients.value.push('');
}
async function submitForm(values){
    try{
        const resp = await http.post('drinks',values)
        if (resp.data.success=== true){
            alert('Sikeres létrehozás\n'+resp.data.data.name)
        }
        else{
            alert("Sikretelen létrehoás\n"+resp.data.message)
        }
    }catch(e){
        alert("Sikretelen létrehoás\n"+e.data.message)
    }
}
const schema = yup.object({
    name: yup.string().max(50, 'Max 50 karakter!').required("<magyar üzenet>"),
    ingredients: yup.string().required("<magyar üzenet>"),
    description: yup.string().required("<magyar üzenet>").max(25, "Max 25 karakter!"),
    quantity: yup.number().min(1).max(100).required(),
    price: yup.number().min(1).max(5000).required(),
    flavor_id: yup.number().required(),
    discounted_price: yup.number().min(1).max(5000).required()
})
onMounted(getData);
</script>

<template>
<main class="m-auto p-3 container">
    <div class="row">
        <div class="col">
            <h1>Új ital létrehozása</h1>
            <hr>
        </div>
    </div>
    <div class="row">
        <div class="col">
            <VForm  @submit="submitForm" :validation-schema="schema">
            <div class="input-group">
                <label for="name" class="input-group-text">Név</label>
                <Field type="text" name="name" id="name" class="form-control"/>
                <ErrorMessage name="name" as="div" class="alert alert-danger"/>
            </div>
            <div class="input-group">
                <label class="input-group-text">Hozzávaló:</label>
                <FieldArray name="ingredients">
                <template v-for="(ingredient, index) in ingredients" :key="index">
                    <Field type="text" :name="'ingredients[' + index + ']'" v-model="ingredients[index]" class="form-control"/>
                    <ErrorMessage :name="'ingredients[' + index + ']'" as="div" class="alert alert-danger"/>
                </template>
                </FieldArray>
                <button class="btn btn-success" type="button" @click="addIngredient"> Hozzávaló hozzadása</button>
            </div>
            <div class="input-group">
                <label for="description" class="input-group-text">Leírás</label>
                <Field type="text" name="description" id="description" class="form-control"/>
                <ErrorMessage name="description" as="div" class="alert alert-danger"/>
            </div>
            <div class="input-group">
                <label for="quantity" class="input-group-text">Mennyiség</label>
                <Field type="number" name="quantity" id="quantity" class="form-control"/>
                <ErrorMessage name="quantity" as="div" class="alert alert-danger"/>
            </div>
            <div class="input-group">
                <label for="price" class="input-group-text">Ár</label>
                <Field type="number" name="price" id="price" class="form-control"/>
                <ErrorMessage name="price" as="div" class="alert alert-danger"/>
            </div>
            <div class="input-group">
                <label for="discounted_price" class="input-group-text">Kedvezményes ár</label>
                <Field type="number" name="discounted_price" id="discounted_price" class="form-control"/>
                <ErrorMessage name="discounted_price" as="div" class="alert alert-danger"/>
            </div>
            <div class="input-group">
                <label class="input-group-text" for="flavor_id">Ízetsítés</label>
                <Field name="flavor_id" id="flavor_id" as="select" class="form-select">
                    <option v-for="flavor in flavors" :key="flavor.id" :value="flavor.id">{{ flavor.name }}</option>
                </Field>
                <ErrorMessage as="div" class="alert alert-danger" name="flavor_id"/>
            </div>
            <button class="btn btn-success mt-2" type="submit">Küldés</button>
        </VForm>
        </div>
    </div>
</main>
</template>

<style scoped>

</style>


