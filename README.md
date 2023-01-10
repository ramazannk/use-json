# use-json

working with JSON.



const rubInput = document.querySelector('.exchange-input'),
      exchangeSelect = document.querySelector('.exchange-select'),
      output = document.querySelector('.exchange-output');

async function  getCurrency(url){
    let res = await fetch(url);
    
    return await res.json();
}

getCurrency('http://localhost:3000/AllCurrency')
    .then(data=>{
        data.map(item=>{
            function convertion(rub, currency){
                console.log(item);
                return rub * item[currency];
            }
            rubInput.addEventListener('input', ()=>{
                const rub = rubInput.value,
                      select = exchangeSelect.value,
                      outPutCurrency = convertion(rub, select);
            
                      output.innerHTML = outPutCurrency;
            
            });
        });
    });







   


