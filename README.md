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
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. NNW_Placowki
    step: "[KROK ŚCIEŻKI]", // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany. Tu - 1.
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    items: [
     {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "Żłobek, przedszkole",
      price: 00.00,
      quantity: 1
    },
    {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "Szkoła podstawowa, szkoła średnia",
      price: 00.00,
      quantity: 1
    },
    {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "Szkoła wyższa, szkoła policealna",
      price: 00.00,
      quantity: 1
    }]
  }
});
```

### 2) Wybranie rodzaju placówki - wywołanie eventu view_item

Prośba o wywołanie kodu w momencie wejścia na strony produktu. Na przykład: https://florina.eu/collections/bestsellery/products/garnek-aluminiowy-nube-20-cm-2-8-l.

![Zrzut ekranu 2024-11-20 132319](https://github.com/user-attachments/assets/834aa1e7-7578-44bb-9640-39d07f9bbe8d)

``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "view_item",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. NNW_Placowki
    step: "[KROK ŚCIEŻKI]", // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany. Tu - 2.
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    items: [
     {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "[NAZWA PLACÓWKI]", // zmienna przekazująca nazwę wybranej placówki, np. "Szkoła wyższa, szkoła policealna"
      price: 00.00,
      quantity: 1
    }
    ]
  }
});
```

### 3) Wybranie rodzaju placówki - wywołanie eventu select_item

Prośba o wywołanie kodu w momencie kliknięcia na nazwę placówki na stronach z listingiem produktu. Na przykład: https://florina.eu/collections/bestsellery/products/garnek-aluminiowy-nube-20-cm-2-8-l.

![Zrzut ekranu 2024-11-20 140239](https://github.com/user-attachments/assets/af7ae5af-2a42-4634-97b8-2c424e0549b9)


``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "select_item",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. NNW_Placowki
    step: "[KROK ŚCIEŻKI]", // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany. Tu - 2.
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    items: [
     {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "[NAZWA PLACÓWKI]", // zmienna przekazująca nazwę wybranej placówki, np. "Szkoła wyższa, szkoła policealna"
      price: 00.00,
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
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. NNW_Placowki
    step: "[KROK ŚCIEŻKI]", // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany. Tu - 3.
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    currency: "PLN",
    value: 00.00,
    items: [
     {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "[NAZWA PLACÓWKI]", // zmienna przekazująca nazwę wybranej placówki, np. "Szkoła wyższa, szkoła policealna"
      price: 00.00,
      quantity: 1,
      number_of_client: [LICZBA OSÓB], // zmienna przekazująca liczbę osób, np. 1
      service_start: "[DATA POCZĄTKOWA]", // zmienna przekazująca datę początku obowiązywania ubezpieczenia, np. "2024-10-30"
      coupon: "[NAZWA KODU PROMOCYJNEGO]", // zmienna przekazująca kod rabatowy. Jeżeli kupony mają klasyfikację, wstawiamy nazwę typu kuponu (np -10%), jeżeli nie 0/1 (czy użyty)
      survey_question_1: "[ODPOWIEDŻ NA PYTANIE 1]", // zmienna 0/1 dla każdego suwaka z pytaniami, gdzie 0 = NIE, 1 = TAK
      survey_question_2: "[ODPOWIEDŻ NA PYTANIE 1]" // zmienna 0/1 dla każdego suwaka z pytaniami, gdzie 0 = NIE, 1 = TAK
    }
    ]
  }
});
```

### 5) Wyświetlenie wariantów - wywołanie eventu view_cart ????

Prośba o wywołanie kodu w momencie wyświetlenia ramki z wariantami na stronie https://moje.pzu.pl/sales/generic/education/variants.

![image](https://github.com/user-attachments/assets/92e68f65-a610-4e23-b487-acc1f166fe83)

``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "view_cart",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. NNW_Placowki
    step: "[KROK ŚCIEŻKI]", // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany. Tu - 4.
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    currency: "PLN",
    value: 304.80,
    items: [
     {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "[NAZWA PLACÓWKI]", // zmienna przekazująca nazwę wybranej placówki, np. "Szkoła wyższa, szkoła policealna"
      item_variant: "1",
      price: 48.40,
      quantity: 1,
      number_of_client: [LICZBA OSÓB], // zmienna przekazująca liczbę osób, np. 1
      service_start: "[DATA POCZĄTKOWA]", // zmienna przekazująca datę początku obowiązywania ubezpieczenia, np. "2024-10-30"
      coupon: "[NAZWA KODU PROMOCYJNEGO]", // zmienna przekazująca kod rabatowy. Jeżeli kupony mają klasyfikację, wstawiamy nazwę typu kuponu (np -10%), jeżeli nie 0/1 (czy użyty)
      survey_question_1: "[ODPOWIEDŻ NA PYTANIE 1]", // zmienna 0/1 dla każdego suwaka z pytaniami, gdzie 0 = NIE, 1 = TAK
      survey_question_2: "[ODPOWIEDŻ NA PYTANIE 1]" // zmienna 0/1 dla każdego suwaka z pytaniami, gdzie 0 = NIE, 1 = TAK
    },
    {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "[NAZWA PLACÓWKI]", // zmienna przekazująca nazwę wybranej placówki, np. "Szkoła wyższa, szkoła policealna"
      item_variant: "2",
      price: 93.30,
      quantity: 1,
      number_of_client: [LICZBA OSÓB], // zmienna przekazująca liczbę osób, np. 1
      service_start: "[DATA POCZĄTKOWA]", // zmienna przekazująca datę początku obowiązywania ubezpieczenia, np. "2024-10-30"
      coupon: "[NAZWA KODU PROMOCYJNEGO]", // zmienna przekazująca kod rabatowy. Jeżeli kupony mają klasyfikację, wstawiamy nazwę typu kuponu (np -10%), jeżeli nie 0/1 (czy użyty)
      survey_question_1: "[ODPOWIEDŻ NA PYTANIE 1]", // zmienna 0/1 dla każdego suwaka z pytaniami, gdzie 0 = NIE, 1 = TAK
      survey_question_2: "[ODPOWIEDŻ NA PYTANIE 1]" // zmienna 0/1 dla każdego suwaka z pytaniami, gdzie 0 = NIE, 1 = TAK
    },
    {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "[NAZWA PLACÓWKI]", // zmienna przekazująca nazwę wybranej placówki, np. "Szkoła wyższa, szkoła policealna"
      item_variant: "3",
      price: 163.10,
      quantity: 1,
      number_of_client: [LICZBA OSÓB], // zmienna przekazująca liczbę osób, np. 1
      service_start: "[DATA POCZĄTKOWA]", // zmienna przekazująca datę początku obowiązywania ubezpieczenia, np. "2024-10-30"
      coupon: "[NAZWA KODU PROMOCYJNEGO]", // zmienna przekazująca kod rabatowy. Jeżeli kupony mają klasyfikację, wstawiamy nazwę typu kuponu (np -10%), jeżeli nie 0/1 (czy użyty)
      survey_question_1: "[ODPOWIEDŻ NA PYTANIE 1]", // zmienna 0/1 dla każdego suwaka z pytaniami, gdzie 0 = NIE, 1 = TAK
      survey_question_2: "[ODPOWIEDŻ NA PYTANIE 1]" // zmienna 0/1 dla każdego suwaka z pytaniami, gdzie 0 = NIE, 1 = TAK
    }
    ]
  }
});
```

### 6) Wejście na stronę Checkouts - wywołanie eventu begin_checkout

Prośba o wywołanie kodu w momencie wejścia na strone Checkouts. Na przykład: https://florina.eu/checkouts/cn/Z2NwLWV1cm9wZS13ZXN0NDowMUpENFYxN1A0WThXRTJRWFRHUTRYUlQ3OQ.

![Zrzut ekranu 2024-11-20 141223](https://github.com/user-attachments/assets/d8424977-e57c-47bc-8e8c-217d76d1d92b)


``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "begin_checkout",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. NNW_Placowki
    step: "[KROK ŚCIEŻKI]", // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany. Tu - 5.
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    currency: "PLN",
    value: [CENA WARIANTU], // zmienna przekazująca wartość wybranego wariantu
    items: [
     {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "[NAZWA PLACÓWKI]", // zmienna przekazująca nazwę wybranej placówki, np. "Szkoła wyższa, szkoła policealna"
      item_variant: "[NUMER WARIANTU]", // zmienna przekazująca numer wybranego wariantu
      price: [CENA WARIANTU], // zmienna przekazująca wartość wybranego wariantu
      quantity: 1,
      number_of_client: [LICZBA OSÓB], // zmienna przekazująca liczbę osób, np. 1
      service_start: "[DATA POCZĄTKOWA]", // zmienna przekazująca datę początku obowiązywania ubezpieczenia, np. "2024-10-30"
      coupon: "[NAZWA KODU PROMOCYJNEGO]", // zmienna przekazująca kod rabatowy. Jeżeli kupony mają klasyfikację, wstawiamy nazwę typu kuponu (np -10%), jeżeli nie 0/1 (czy użyty)
      survey_question_1: "[ODPOWIEDŻ NA PYTANIE 1]", // zmienna 0/1 dla każdego suwaka z pytaniami, gdzie 0 = NIE, 1 = TAK
      survey_question_2: "[ODPOWIEDŻ NA PYTANIE 1]", // zmienna 0/1 dla każdego suwaka z pytaniami, gdzie 0 = NIE, 1 = TAK
      quotationID: "T13754097"
    },
    ]
  }
});
```

### 7) Wybór odpowiedniej metody dostawy na stronie Checkouts - wywołanie eventu add_shipping_info

Prośba o wywołanie kodu w momencie pojawienia na stronie Checkouts predefiniowanej metody dostawy lub wybór jednej z opcji, jeżeli taka opcja bedzie. Na przykład: https://florina.eu/checkouts/cn/Z2NwLWV1cm9wZS13ZXN0NDowMUpENFYxN1A0WThXRTJRWFRHUTRYUlQ3OQ.

![Zrzut ekranu 2024-11-20 141702](https://github.com/user-attachments/assets/05461fc4-b26a-4585-afca-088f77acbd6e)

``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "add_shipping_info",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. NNW_Placowki
    step: "[KROK ŚCIEŻKI]", // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany. Tu - 6.
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    currency: "PLN",
    value: [CENA WARIANTU], // zmienna przekazująca wartość wybranego wariantu
    shipping_tier: "virtual",
    items: [
     {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "[NAZWA PLACÓWKI]", // zmienna przekazująca nazwę wybranej placówki, np. "Szkoła wyższa, szkoła policealna"
      item_variant: "[NUMER WARIANTU]", // zmienna przekazująca numer wybranego wariantu
      price: [CENA WARIANTU], // zmienna przekazująca wartość wybranego wariantu
      quantity: 1,
      number_of_client: [LICZBA OSÓB], // zmienna przekazująca liczbę osób, np. 1
      service_start: "[DATA POCZĄTKOWA]", // zmienna przekazująca datę początku obowiązywania ubezpieczenia, np. "2024-10-30"
      coupon: "[NAZWA KODU PROMOCYJNEGO]", // zmienna przekazująca kod rabatowy. Jeżeli kupony mają klasyfikację, wstawiamy nazwę typu kuponu (np -10%), jeżeli nie 0/1 (czy użyty)
      survey_question_1: "[ODPOWIEDŻ NA PYTANIE 1]", // zmienna 0/1 dla każdego suwaka z pytaniami, gdzie 0 = NIE, 1 = TAK
      survey_question_2: "[ODPOWIEDŻ NA PYTANIE 1]", // zmienna 0/1 dla każdego suwaka z pytaniami, gdzie 0 = NIE, 1 = TAK
      quotationID: "T13754097"
    },
    ]
  }
});
```

### 8) Wybór sposobu płatności na stronie Checkouts - wywołanie eventu add_payment_info

Prośba o wywołanie kodu w momencie pojawienia na stronie Checkouts predefiniowanej metody płatności lub wybór jednej z opcji, jeżeli taka opcja bedzie. Na przykład: https://florina.eu/checkouts/cn/Z2NwLWV1cm9wZS13ZXN0NDowMUpENFYxN1A0WThXRTJRWFRHUTRYUlQ3OQ.

![Zrzut ekranu 2024-11-20 142538](https://github.com/user-attachments/assets/13b7fa46-1326-49ba-96d2-cda5c66b1654)


``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "add_payment_info",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. NNW_Placowki
    step: "[KROK ŚCIEŻKI]", // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany. Tu - 8.
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    currency: "PLN",
    value: [WARTOŚĆ], // zmienna przekazująca wartość do zapłaty
    shipping_tier: "virtual",
    payment_type: "[METODA PŁATNOŚCI]", // zmienna przekazująca wybraną metodę płatności
    items: [
     {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "[NAZWA PLACÓWKI]", // zmienna przekazująca nazwę wybranej placówki, np. "Szkoła wyższa, szkoła policealna"
      item_variant: "[NUMER WARIANTU]", // zmienna przekazująca numer wybranego wariantu
      price: [CENA WARIANTU], // zmienna przekazująca wartość wybranego wariantu
      quantity: 1,
      number_of_client: [LICZBA OSÓB], // zmienna przekazująca liczbę osób, np. 1
      service_start: "[DATA POCZĄTKOWA]", // zmienna przekazująca datę początku obowiązywania ubezpieczenia, np. "2024-10-30"
      coupon: "[NAZWA KODU PROMOCYJNEGO]", // zmienna przekazująca kod rabatowy. Jeżeli kupony mają klasyfikację, wstawiamy nazwę typu kuponu (np -10%), jeżeli nie 0/1 (czy użyty)
      quotationID: "T13754097"
    },
    ]
  }
});


### 9) Faktyczne utworzenie transakcji w systemie - wywołanie eventu purchase

Prośba o wywołanie kodu w momencie faktycznego utworzenia transakcji w systemie, po kliknięciu w przycisk "Pay now". Na przykład: https://florina.eu/checkouts/cn/Z2NwLWV1cm9wZS13ZXN0NDowMUpENFYxN1A0WThXRTJRWFRHUTRYUlQ3OQ

![Zrzut ekranu 2024-11-20 144623](https://github.com/user-attachments/assets/47a82baf-4cb3-44d9-b55c-df62b2e1c045)

``` javascript
dataLayer.push({ ecommerce: null });  // Clear the previous ecommerce object.
dataLayer.push({
  event: "purchase",
  ecommerce: {
    item_list_id: "[NUMER LISTINGU]", // id listingu, jeżeli jest dostępne
    item_list_name: "[NAZWA LISTINGU]", // zmienna przekazująca nazwę listingu, np. NNW_Placowki
    step: "[KROK ŚCIEŻKI]", // zmienna przekazująca krok ścieżki, na którym dany event jest wywołany. Tu - 8.
    affiliation: "[PARAMETR WEJŚCIA]", // zmienna przekazująca parametr z sessionstorage lub cookie
    is_logged: "[STATUS ZALOGOWANIA]", // zmienna przekazująca informację czy użytkownik jest zalogowany, np. true/false
    currency: "PLN",
    value: [WARTOŚĆ], // zmienna przekazująca wartość do zapłaty
    shipping_tier: "virtual",
    payment_type: "[METODA PŁATNOŚCI]", // zmienna przekazująca wybraną metodę płatności
    transaction_id: [NUMER ZAMÓWIENIA], //zmienna przekazująca id zamówienia
    items: [
     {
      item_id: "Szkolne_v1", 
      item_name: "NNW Szkolne",
      item_brand: "PZU",
      item_category: "Majątek/Podróże",
      item_category2: "NNW Szkolne",
      item_category3: "[NAZWA PLACÓWKI]", // zmienna przekazująca nazwę wybranej placówki, np. "Szkoła wyższa, szkoła policealna"
      item_variant: "[NUMER WARIANTU]", // zmienna przekazująca numer wybranego wariantu
      price: [CENA WARIANTU], // zmienna przekazująca wartość wybranego wariantu
      quantity: 1,
      number_of_client: [LICZBA OSÓB], // zmienna przekazująca liczbę osób, np. 1
      service_start: "[DATA POCZĄTKOWA]", // zmienna przekazująca datę początku obowiązywania ubezpieczenia, np. "2024-10-30"
      coupon: "[NAZWA KODU PROMOCYJNEGO]", // zmienna przekazująca kod rabatowy. Jeżeli kupony mają klasyfikację, wstawiamy nazwę typu kuponu (np -10%), jeżeli nie 0/1 (czy użyty)
      quotationID: "T13754097"
    },
    ]
