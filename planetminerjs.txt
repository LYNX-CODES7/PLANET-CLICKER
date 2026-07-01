let prices = {
  stone: 10,
  silver: 50,
  iron: 100,
  gold: 300,
  platinum: 750,
  diamond: 1500,
  uranium: 5000,
  singularityShards: 50000,
  antimatter: 100000
}
let planet = 0
let fuel = 0
let travelCost = 1000000
let fuelCost = 1000000
let upgradeCost3 = 300000
let upgradeCost2 = 100000
let upgradeCost1 = 30000
let minesPerClick = 1
const fuelText = document.getElementById("fuelText")
const fuelButton = document.getElementById("fuelButton")
const upgradeButton2 = document.getElementById("upgradeButton2")
const upgradeButton3 = document.getElementById("upgradeButton3")
const multiplierText = document.getElementById("multiplierText")
const companyLevel = document.getElementById("companyLevel")
const upgradeButton1 = document.getElementById("upgradeButton1")
const sellAllButton = document.getElementById("sellAllButton")
sellAllButton.addEventListener("click", function () {
  sellAll()
  message.textContent = "Sold All Resources"
})
let roll
const moneyCount = document.getElementById("moneyCount")
let money = 0
function updateMoney() {
moneyCount.textContent = `$${money}`
}
updateMoney()
function sellAll(){
 for (let resource in resources) {
  money += resources[resource] * prices[resource]
  resources[resource] = 0
 }


updateResources()
updateMoney()
   } 

function updateResources() {
  stoneCount.textContent = resources.stone
silverCount.textContent = resources.silver
ironCount.textContent = resources.iron
goldCount.textContent = resources.gold
platinumCount.textContent = resources.platinum
diamondCount.textContent = resources.diamond
uraniumCount.textContent = resources.uranium
singularityShardCount.textContent = resources.singularityShards
antimatterCount.textContent = resources.antimatter
}
let resources = {
  stone: 0,
  silver: 0,
  iron: 0,
  gold: 0,
  platinum: 0,
  diamond: 0,
  uranium: 0,
  singularityShards: 0,
  antimatter: 0,

}
const stoneCount = document.getElementById("stoneCount")
const silverCount = document.getElementById("silverCount")
const ironCount = document.getElementById("ironCount")
const goldCount = document.getElementById("goldCount")
const platinumCount = document.getElementById("platinumCount")
const diamondCount = document.getElementById("diamondCount")
const uraniumCount = document.getElementById("uraniumCount")
const singularityShardCount = document.getElementById("singularityShardCount")
const antimatterCount = document.getElementById("antimatterCount")
const mineButton = document.getElementById("mineButton")
mineButton.addEventListener("click", function mineOnce() {
  roll = Math.random()
for (let i = 0; i < minesPerClick; i++){

if (roll < 0.50){
  resources.stone++
  message.textContent = "You found stone!"
}
else if (roll < 0.70){
  resources.silver++
  message.textContent = "You found silver!";
}
else if (roll < 0.90){
  resources.iron++
  message.textContent = "You found iron!"
}
else if (roll < 0.95){
resources.gold++
message.textContent = "You found gold!"
}
else if (roll < 0.97){
resources.platinum++
message.textContent = "You found platinum!";
}
else if (roll < 0.99){
  resources.diamond++
  message.textContent = "You found diamond!";
}
else if (roll < 0.992){
  resources.uranium++
  message.textContent = "Cool! You found uranium!"
}
else if (roll < 0.999){
  resources.singularityShards++
  message.textContent = "Awesome! You found a singularity shard!"
}
else {
  resources.antimatter++
  message.textContent = "What have you done...? You found antimatter...";
}
updateResources()
}})
upgradeButton1.addEventListener("click", function (){
if (money >= upgradeCost1){
minesPerClick += 1
money -= upgradeCost1
upgradeCost1 = Infinity
updateMoney()
updateResources()
multiplierText.textContent = minesPerClick
upgradeButton1.textContent = "Purchased"
message.textContent = ("Upgrade Purchased")
}
else if (upgradeCost1 == Infinity){
  message.textContent = ("Upgrade Already Purchased")
}
else if (money < upgradeCost1){
  message.textContent = "Insufficient Funds"

}})
upgradeButton2.addEventListener("click", function (){
if (money >= upgradeCost2){
minesPerClick += 1
money -= upgradeCost2
upgradeCost2 = Infinity
updateMoney()
updateResources()
multiplierText.textContent = minesPerClick
upgradeButton2.textContent = "Purchased"
message.textContent = ("Upgrade Purchased")
}
else if (upgradeCost2 == Infinity){
  message.textContent = ("Upgrade Already Purchased")
}
else if (money < upgradeCost2){
  message.textContent = "Insufficient Funds"

}})
  upgradeButton3.addEventListener("click", function (){
if (money >= upgradeCost3){
minesPerClick += 2
money -= upgradeCost3
upgradeCost3 = Infinity
updateMoney()
updateResources()
multiplierText.textContent = minesPerClick
upgradeButton3.textContent = "Purchased"
message.textContent = ("Upgrade Purchased")
}
else if (upgradeCost3 == Infinity){
  message.textContent = ("Upgrade Already Purchased")
}
else if (money < upgradeCost3){
  message.textContent = "Insufficient Funds"

}})
  
fuelButton.addEventListener("click", function (){
if (money >= fuelCost){
money -= fuelCost
fuel += 500000
fuelText.textContent = fuel
updateMoney()
updateResources()

multiplierText.textContent = minesPerClick

message.textContent = ("Fuel Purchased")
}
else if (money < fuelCost){
  message.textContent = "Insufficient Funds"
}})
  travelButton.addEventListener("click", function (){
if (fuel >= travelCost){
fuel -= travelCost
updateMoney()
updateResources()
minesPerClick += 50
travelCost = Infinity
travelButton.textContent = "Purchased"
multiplierText.textContent = minesPerClick
planet += 1
fuelText.textContent = fuel
message.textContent = ("Travelled To Space")
}
else if (travelCost == Infinity){
  travelButton.textContent = "Purchased"
}
else if (fuel < travelCost){
  message.textContent = "Insufficient Fuel"
  
}})
if (money >= 100000000){
  message.textContent = "You got $100M! You Win!"
}




