# use-json

working with JSON.


function exchangeCurrency(input, select, outPutCurrency){
    const rubInput = document.querySelector(input),
          exchangeSelect = document.querySelector(select),
          output = document.querySelector(outPutCurrency);

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

}
exchangeCurrency('.exchange-input', '.exchange-select', '.exchange-output')





   


