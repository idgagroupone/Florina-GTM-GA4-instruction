# Specyfikacja Google Tag Manager
Skopiuj poniższy kod i wklej go na każdej stronie swojej witryny.

### 1) Sekcja "head"

Prośba o wklejenie kodu tak wysoko w sekcji ``` <head> ``` strony, jak to możliwe

``` javascript
<!-- Google Tag Manager -->
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-5RPRHR3');</script>
<!-- End Google Tag Manager -->
```

### 2) Tag "body"

Prośba o wklejenie kodu bezpośrednio po otwierającym tagu ```<body>```

``` javascript
<!-- Google Tag Manager (noscript) -->
<noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-5RPRHR3"
height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
<!-- End Google Tag Manager (noscript) -->
```

# Specyfikacja dataLayer
Prośba o wstawienie DataLayerów na serwis https://florina.eu/. 

Przydatne linki:

https://developers.google.com/analytics/devguides/collection/ga4/reference/events

## Pełna dokumentacja dataLayer

### 1) Wyświetlenie listingu produktów - wywołanie eventu view_item_list

Prośba o wywołanie kodu w momencie wyświetlenia strony z listingiem produktów na stronie https://florina.eu/collections/bestsellery.
![Zrzut ekranu 2024-11-20 131829](https://github.com/user-attachments/assets/832ac9ad-a3cd-4063-bc47-be79da54b991)


``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "view_item_list",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. Bestsellery
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    userID: "4873957", // ID użytkownika. Wartość powinna być dostępna przy logowaniu do serwisu i odpowiadać numerowi z CRM.
    items: [
     {
      item_id: "SKU_12345", 
      item_name: "garnek-aluminiowy-nube-20-cm-2-8-l",
      item_brand: "Florina",
      item_category: "Bestsellery",
      item_category2: "Florina Nube",
      item_category3: "",
      item_variant: "green",
      currency: "PLN",
      price: 30.00,
      quantity: 1
    },
    {
      item_id: "SKU_123456", 
      item_name: "Patelnia aluminiowa 28 cm",
      item_brand: "Florina",
      item_category: "Patelnie",
      item_category2: "Florina Nube",
      item_category3: "",
      item_variant: "green",
      currency: "PLN",
      price: 30.00,
      quantity: 1
    }]
  }
});
```

### 2) Wejście na stronę produktu - wywołanie eventu view_item

Prośba o wywołanie kodu w momencie wejścia na strony produktu. Na przykład: https://florina.eu/collections/bestsellery/products/garnek-aluminiowy-nube-20-cm-2-8-l.

![Zrzut ekranu 2024-11-20 132319](https://github.com/user-attachments/assets/834aa1e7-7578-44bb-9640-39d07f9bbe8d)

``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "view_item",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. Bestsellery
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    userID: "4873957", // ID użytkownika. Wartość powinna być dostępna przy logowaniu do serwisu i odpowiadać numerowi z CRM.
    items: [
     {
      item_id: "SKU_12345", 
      item_name: "garnek-aluminiowy-nube-20-cm-2-8-l",
      item_brand: "Florina",
      item_category: "Bestsellery",
      item_category2: "Florina Nube",
      item_category3: "",
      item_variant: "green",
      currency: "PLN",
      price: 30.00,
      quantity: 1
    }
    ]
  }
});
```

### 3) Kliknięcie w konkretny produkt - wywołanie eventu select_item

Prośba o wywołanie kodu w momencie kliknięcia na nazwę placówki na stronach z listingiem produktu. Na przykład: https://florina.eu/collections/bestsellery/products/garnek-aluminiowy-nube-20-cm-2-8-l.

![Zrzut ekranu 2024-11-20 140239](https://github.com/user-attachments/assets/af7ae5af-2a42-4634-97b8-2c424e0549b9)


``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "select_item",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. Bestsellery
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    userID: "4873957", // ID użytkownika. Wartość powinna być dostępna przy logowaniu do serwisu i odpowiadać numerowi z CRM.
    items: [
     {
      item_id: "SKU_12345", 
      item_name: "garnek-aluminiowy-nube-20-cm-2-8-l",
      item_brand: "Florina",
      item_category: "Bestsellery",
      item_category2: "Florina Nube",
      item_category3: "",
      item_variant: "green",
      currency: "PLN",
      price: 30.00,
      quantity: 1
    }
    ]
  }
});
```

### 4) Kliknięcie w przycisk "Add to cart" - wywołanie eventu add_to_cart

Prośba o wywołanie kodu w momencie kliknięcia w przycisk "Add to cart" na stronach produktu. Na przykład: https://florina.eu/collections/frontpage/products/florina-amvegan-6.

![Zrzut ekranu 2024-11-20 140517](https://github.com/user-attachments/assets/e8d1d567-8bcc-45e1-8577-5851fa2fd309)

``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "add_to_cart",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. Bestsellery
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    userID: "4873957", // ID użytkownika. Wartość powinna być dostępna przy logowaniu do serwisu i odpowiadać numerowi z CRM.
    currency: "[WALUTA]", // zmienna przekazująca walutę powiązaną ze zdarzeniem podana w 3-literowym formacie ISO 4217
    value: 30.00,
    items: [
     {
      item_id: "SKU_12345", 
      item_name: "garnek-aluminiowy-nube-20-cm-2-8-l",
      item_brand: "Florina",
      item_category: "Bestsellery",
      item_category2: "Florina Nube",
      item_category3: "",
      item_variant: "green",
      currency: "PLN",
      price: 30.00,
      quantity: 1
    }
    ]
  }
});
```

### 5) Wejście na stronę Checkouts - wywołanie eventu begin_checkout

Prośba o wywołanie kodu w momencie wejścia na strone Checkouts. Na przykład: https://florina.eu/checkouts/cn/Z2NwLWV1cm9wZS13ZXN0NDowMUpENFYxN1A0WThXRTJRWFRHUTRYUlQ3OQ.

![Zrzut ekranu 2024-11-20 141223](https://github.com/user-attachments/assets/d8424977-e57c-47bc-8e8c-217d76d1d92b)


``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "begin_checkout",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. Bestsellery
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    userID: "4873957", // ID użytkownika. Wartość powinna być dostępna przy logowaniu do serwisu i odpowiadać numerowi z CRM.
    currency: "[WALUTA]", // zmienna przekazująca walutę powiązaną ze zdarzeniem podana w 3-literowym formacie ISO 4217
    value: 30.00, // zmienna przekazująca wartość całego koszyka
    items: [
         {
      item_id: "SKU_12345", 
      item_name: "garnek-aluminiowy-nube-20-cm-2-8-l",
      item_brand: "Florina",
      item_category: "Bestsellery",
      item_category2: "Florina Nube",
      item_category3: "",
      item_variant: "green",
      currency: "PLN",
      price: 30.00,
      quantity: 1
    }
    ]
  }
});
```

### 6) Wybór odpowiedniej metody dostawy na stronie Checkouts - wywołanie eventu add_shipping_info

Prośba o wywołanie kodu w momencie pojawienia na stronie Checkouts predefiniowanej metody dostawy lub wybór jednej z opcji, jeżeli taka opcja bedzie. Na przykład: https://florina.eu/checkouts/cn/Z2NwLWV1cm9wZS13ZXN0NDowMUpENFYxN1A0WThXRTJRWFRHUTRYUlQ3OQ.

![Zrzut ekranu 2024-11-20 141702](https://github.com/user-attachments/assets/05461fc4-b26a-4585-afca-088f77acbd6e)

``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "add_shipping_info",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. Bestsellery
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    userID: "4873957", // ID użytkownika. Wartość powinna być dostępna przy logowaniu do serwisu i odpowiadać numerowi z CRM.
    currency: "[WALUTA]", // zmienna przekazująca walutę powiązaną ze zdarzeniem podana w 3-literowym formacie ISO 4217
    value: 30.00, // zmienna przekazująca wartość całego koszyka
    shipping_tier: "Standard", // zmienna przekazująca wybrany sposób dostawy
    items: [
     {
      item_id: "SKU_12345", 
      item_name: "garnek-aluminiowy-nube-20-cm-2-8-l",
      item_brand: "Florina",
      item_category: "Bestsellery",
      item_category2: "Florina Nube",
      item_category3: "",
      item_variant: "green",
      currency: "PLN",
      price: 30.00,
      quantity: 1
    }
    ]
  }
});
```

### 7) Wybór sposobu płatności na stronie Checkouts - wywołanie eventu add_payment_info

Prośba o wywołanie kodu w momencie pojawienia na stronie Checkouts predefiniowanej metody płatności lub wybór jednej z opcji, jeżeli taka opcja bedzie. Na przykład: https://florina.eu/checkouts/cn/Z2NwLWV1cm9wZS13ZXN0NDowMUpENFYxN1A0WThXRTJRWFRHUTRYUlQ3OQ.

![Zrzut ekranu 2024-11-20 142538](https://github.com/user-attachments/assets/13b7fa46-1326-49ba-96d2-cda5c66b1654)


``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "add_payment_info",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. NNW_Placowki
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    userID: "4873957", // ID użytkownika. Wartość powinna być dostępna przy logowaniu do serwisu i odpowiadać numerowi z CRM.
    currency: "[WALUTA]", // zmienna przekazująca walutę powiązaną ze zdarzeniem podana w 3-literowym formacie ISO 4217
    value: 30.00, // zmienna przekazująca wartość całego koszyka
    shipping_tier: "[SPOSÓB DOSTAWY]", // zmienna przekazująca wybrany sposób dostawy
    payment_type: "[METODA PŁATNOŚCI]", // zmienna przekazująca wybraną metodę płatności
    items: [
     {
      item_id: "SKU_12345", 
      item_name: "garnek-aluminiowy-nube-20-cm-2-8-l",
      item_brand: "Florina",
      item_category: "Bestsellery",
      item_category2: "Florina Nube",
      item_category3: "",
      item_variant: "green",
      currency: "PLN",
      price: 30.00,
      quantity: 1
    }
    ]
  }
});
```

### 8) Faktyczne utworzenie transakcji w systemie - wywołanie eventu purchase

Prośba o wywołanie kodu w momencie faktycznego utworzenia transakcji w systemie, po kliknięciu w przycisk "Pay now". Na przykład: https://florina.eu/checkouts/cn/Z2NwLWV1cm9wZS13ZXN0NDowMUpENFYxN1A0WThXRTJRWFRHUTRYUlQ3OQ

![Zrzut ekranu 2024-11-20 144623](https://github.com/user-attachments/assets/47a82baf-4cb3-44d9-b55c-df62b2e1c045)

``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "purchase",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. NNW_Placowki
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    userID: "4873957", // ID użytkownika. Wartość powinna być dostępna przy logowaniu do serwisu i odpowiadać numerowi z CRM.
    currency: "[WALUTA]", // zmienna przekazująca walutę powiązaną ze zdarzeniem podana w 3-literowym formacie ISO 4217
    value: [WARTOŚĆ], // zmienna przekazująca wartość do zapłaty
    shipping_tier: "[SPOSÓB DOSTAWY]", // zmienna przekazująca wybrany sposób dostawy
    payment_type: "[METODA PŁATNOŚCI]", // zmienna przekazująca wybraną metodę płatności
    transaction_id: [NUMER ZAMÓWIENIA], //zmienna przekazująca id zamówienia
    coupon: "[KUPON]", //zmienna przekazująca użyty kupon, jeżeli nie było użytego kupony to ustawić ""
    tax: [WARTOŚĆ VAT], // zmienna przekazująca koszty podatkowe powiązane z transakcją
    shipping: [WARTOŚĆ DOSTAWY], // zmienna przekazująca koszt dostawy powiązany z transakcją
    items: [
     {
      item_id: "SKU_12345", 
      item_name: "garnek-aluminiowy-nube-20-cm-2-8-l",
      item_brand: "Florina",
      item_category: "Bestsellery",
      item_category2: "Florina Nube",
      item_category3: "",
      item_variant: "green",
      currency: "PLN",
      price: 30.00,
      quantity: 1
    }
    ]
  }
});
```
### 9) Załogowanie na platformie - wywołanie eventu login

Prośba o wywołanie kodu w momencie prawidłowego łogowania na platformie. Może być od razu po kliknięciu w przycisk "Sign in". Na przykład: https://florina.eu/account/login

![Zrzut ekranu 2024-11-21 141840](https://github.com/user-attachments/assets/61c02975-6ce5-4dee-8cd2-8e0c24f5e5e8)

``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "login",
  userID: "4873957", // ID użytkownika. Wartość powinna być dostępna przy logowaniu do serwisu i odpowiadać numerowi z CRM.
});
```

### 10) Rejestracja na platformie - wywołanie eventu sign_up

Prośba o wywołanie kodu w momencie prawidłowej rejestracji na platformie. Może być od razu po kliknięciu w przycisk "CREATE". Na przykład: https://florina.eu/account/register

![Zrzut ekranu 2024-11-21 142524](https://github.com/user-attachments/assets/2dfc5eaf-821a-458b-b3cf-d76a81aae491)


``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "sign_up",
  userID: "4873957", // ID użytkownika. Wartość powinna być dostępna przy logowaniu do serwisu i odpowiadać numerowi z CRM.
});
```





