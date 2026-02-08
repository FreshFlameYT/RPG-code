Copyright 2026 FreshFlameYT

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```js
//setTargetState code by _Will__Treaty_	
function setTargetState(id) {
  api.setMobSetting(id, 'idleSound', null)
  api.setMobSetting(id, 'hurtSound', null)
  api.setMobSetting(id, 'baseWalkingSpeed', 0)
  api.setMobSetting(id, 'baseRunningSpeed', 0)
  api.setMobSetting(id, 'jumpCount', 0)
  api.setTargetedPlayerSettingForEveryone(id, 'opacity', 0, true)
} 
//RPG code by FreshFlameYT

function RPG(x,y,z){
let mobId = undefined
let target = undefined
mobId = api.attemptSpawnMob('Draugr Knight', x, y+20, z, {
    name: 'Bot '
});
target = api.attemptSpawnMob('Pig', x, y, z, {
    name: 'Bot '
});

try{
setTargetState(mobId)
setTargetState(target)
api.applyMeleeHit(target, mobId, [0,0,0], undefined, undefined)
api.setMobSetting(mobId,"attackItemName", "RPG");
api.setMobSetting(mobId, 'attackInterval', 200000000);
    api.setMobSetting(mobId, 'attackRadius', 100); 
api.setMobSetting(mobId, "onDeathItemDrops", [
        {
            itemName: "Knight Heart",
            probabilityOfDrop: 0 ,
            dropMinAmount: 0,
            dropMaxAmount: 1,
        }
    ])


setTimeout(() =>api.despawnMob(mobId), 3000)
setTimeout(() =>api.despawnMob(target), 3000)
}catch (error) {
  
  console.log("RPG failed")
}
}


//setTimeout code by _Will__Treaty_	


const _t = {timeouts: new Map(), intervals: new Map(), id: 1}

function setTimeout(cb, delay) {
    const id = _t.id++
    _t.timeouts.set(id, {cb, at: Date.now() + delay})
    return id
}

function clearTimeout(id) {
    _t.timeouts.delete(id)
}

function setInterval(cb, interval) {
    const id = _t.id++
    _t.intervals.set(id, {cb, interval, at: Date.now() + interval})
    return id
}

function clearInterval(id) {
    _t.intervals.delete(id)
}

const _origTick = typeof tick === 'function' ? tick : null

tick = (ms) => {
    if (_origTick) _origTick(ms)
    const now = Date.now()
    for (const [id, t] of _t.timeouts.entries()) {
        if (now >= t.at) {
            try { t.cb() } catch (e) { api.log("Timer error:", e) }
            _t.timeouts.delete(id)
        }
    }
    for (const [id, t] of _t.intervals.entries()) {
        if (now >= t.at) {
            try { t.cb() } catch (e) { api.log("Timer error:", e) }
            t.at = now + t.interval
        }
    }
}
function randomName(){
start
end}
```
