# jest-scratch 
Some scratch notes for when I was implementing jest into vue (code is incomplete)

## jest.config.js 
Create jest.config.js at the same level as package.json
```
module.exports = {
  preset: '@vue/cli-plugin-unit-jest',
  testMatch:  ["**/*.unit.test.js"]  //This will let jest automatically search your directory and run any files ending with unit.test.js
   //I would like to organize the test files in the same directory of the components to test so. 
};
```
## package.json 

Install jest by running
```
npm install --save-dev @vue/test-utils vue-jest 
```
Add this to the scripts part 
```
scripts:{
  "test": "jest --verbose"   // now you can do "npm test" in the command line 
}
```
## BaseTokenSelectDropdown.unit.test.js
### Random unfinished jest test files 
```
import vuetify from 'vuetify';
import Vuex from 'vuex';

import {mount, createLocalVue, shallowMount} from '@vue/test-utils';
import BaseTokenSelectDropdown from "@/components/common/atoms/BaseTokenSelectDropdown";

const localVue = createLocalVue();
localVue.use(Vuex);

describe('BaseTokenSelectDropdown.vue', () => {
    let wrapper;
    let masterState;
    let userState;
    let store;

    beforeEach(() => {
        const localVue = createLocalVue();
        masterState = {
            tokenType: tokenType
        };
        userState = {
            loginUserBasicInfo: {defaultTokenId: "cff54cc8-d95f-fca4-2b77-e87404313625"}
        };
        store = new Vuex.Store({
            modules: {
                master: {masterState},
                user: {userState}
            }
        });
        wrapper = shallowMount(BaseTokenSelectDropdown, {localVue});
    });

    it('is a Vue instance', () => {
        const wrappertwo = shallowMount(BaseTokenSelectDropdown, { store, localVue });
        expect(wrappertwo.isVueInstance()).toBeTruthy();
    });
    // it('has a button', () => {
    //     expect(wrapper.contains('button')).toBe(true)
    // });
});

const tokenType = [{
    "tokenId": "b5398dc8-4eb0-bb77-308e-28289a58655a",
    "displayName": "DEVELOPMENT",
   
}, {
    "tokenId": "cff54cc8-d95f-fca4-2b77-e87404313625",
    "displayName": "CLOUD",
}
 ```

## Links 
- [Vue-test-utils](https://vue-test-utils.vuejs.org/guides/#getting-started): Vue's official documentation and tool for using jest with vue. 
- [Vuetify](https://next.vuetifyjs.com/en/getting-started/unit-testing/#spec-tests): Vuetify's documentation on using jest. 
