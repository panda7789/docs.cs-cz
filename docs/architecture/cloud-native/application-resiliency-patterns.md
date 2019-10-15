---
title: Vzory odolnosti aplikací
description: Architekt cloudových nativních aplikací .NET pro Azure | Vzory odolnosti aplikací
ms.date: 06/30/2019
ms.openlocfilehash: 67ae20f14a67f3a96d6c74cad727afe680ff3178
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315951"
---
# <a name="application-resiliency-patterns"></a>Vzory odolnosti aplikací

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

První linií obrany je odolnost aplikace s podporou softwaru. 

I když můžete investovat do svého vlastního rozhraní odolného proti chybám, takové produkty už existují. [Polly](http://www.thepollyproject.org/) je například komplexní odolnost proti chybám .NET a knihovnou s přechodným zpracováním chyb, která vývojářům umožňuje vyjádřit zásady odolnosti proti chybám v rámci technologie Fluent a bezpečných pro přístup z více vláken. Polly cílí na aplikace sestavené s úplnými .NET Framework nebo .NET Core. Obrázek 6-2 ukazuje zásady odolnosti (tj. funkce) dostupné v knihovně Polly. Tyto zásady je možné použít individuálně nebo společně.

![Polly Framework](./media/polly-resiliency-framework.png)

**Obrázek 6-2**. Funkce architektury Polly odolné proti chybám

Všimněte si, jak je uvedeno výše v předchozím obrázku zásady odolnosti platí pro zprávy s požadavkem, ať už přicházejí z externího klienta nebo jiné back-endové služby. Cílem je kompenzovat žádost o službu, která může být v nedostupném případě. Tato krátká přerušení obvykle nahlásí stavové kódy HTTP zobrazené na obrázku 6-3.

![Stavové kódy HTTP pro opakování](./media/http-status-codes.png)

**Obrázek 6-3**. Stavové kódy HTTP pro opakování

Otázka: budete opakovat kód stavu HTTP 403 – zakázáno? Ne. V tomto případě systém pracuje správně, ale informuje volajícího, že nemá oprávnění k provedení požadované operace. Je nutné vzít v potaz pouze operace způsobené chybami.

Jak je popsáno v kapitole 1, vývojáři Microsoftu vytvářející cloudové nativní aplikace by měli cílit na .NET Core. Verze 2,1 zavedla knihovnu [HTTPClientFactory](https://www.stevejgordon.co.uk/introduction-to-httpclientfactory-aspnetcore) pro vytváření instancí klienta http pro interakci s prostředky založenými na adrese URL. Nahrazení původní třídy HTTPClient, třída Factory podporuje mnoho rozšířených funkcí, jedna z nich je [těsná integrace](../microservices/implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md) s knihovnou odolnosti Polly. Díky tomu můžete snadno definovat zásady odolnosti ve třídě spuštění aplikace, aby se mohla zpracovávat částečná selhání a problémy s připojením.

Teď se podíváme na vzory pokusů o opakování a okruhu.

### <a name="retry-pattern"></a>Vzor opakování

V distribuovaném cloudovém nativním prostředí můžou volání služeb a cloudových prostředků selhat kvůli přechodným (krátkodobým) chybám, které se obvykle po krátké době vyřeší. Implementace strategie opakování pomáhá cloudovým nativním službám zvládnout tyto scénáře.

[Vzor opakování](https://docs.microsoft.com/azure/architecture/patterns/retry) umožňuje službě opakovat operaci neúspěšné žádosti a (konfigurovatelný) kolikrát s exponenciálně rostoucí čekací dobou. Obrázek 6-4 ukazuje opakování v akci.

![Vzor opakování v akci](./media/retry-pattern.png)

**Obrázek 6-4**. Vzor opakování v akci

Na předchozím obrázku byl pro operaci požadavku implementován vzor opakování. Je nakonfigurovaná tak, aby umožňovala až čtyři opakované pokusy, před selháním s intervalem omezení rychlosti (čekací doba) od 2 sekund, který exponenciálně zdvojnásobuje při každém dalším pokusu.

- První vyvolání se nezdařilo a vrátí stavový kód HTTP 500. Aplikace počká po dobu dvou sekund a zopakuje volání.
- Druhé vyvolání také nefunguje a vrátí stavový kód HTTP 500. Aplikace nyní zdvojnásobí omezení rychlosti interval na čtyři sekundy a zopakuje volání.
- Nakonec se třetí volání zdaří.
- V tomto scénáři by se pokus o operaci opakování při zdvojnásobení omezení rychlosti doby před selháním tohoto volání pokusil o čtyři opakované pokusy.

Je důležité zvýšit omezení rychlosti období před opakovaným pokusem o volání, aby bylo možné čas služby samočinně opravovat. Osvědčeným postupem je implementovat exponenciálně rostoucí omezení rychlosti (zdvojnásobit periodu při každém opakování), aby se povolila adekvátní doba opravy.

## <a name="circuit-breaker-pattern"></a>Vzorek pro přerušení okruhu

I když vzor opakování může přispět k vyřazení žádosti entangled v částečném selhání, existují situace, kdy selhání může být způsobeno neočekávanými událostmi, které budou vyžadovat přeložení delší dobu. Tyto chyby můžou být v rozsahu závažnosti od částečné ztráty připojení k úplnému selhání služby. V těchto situacích je bezúčelné pro aplikaci, aby se nepřetržitě opakovala operace, která není pravděpodobně úspěšná.

Kvůli horšímu provádění operací nepřetržitého opakování při opakovaném pokusu o nereagující službu vás může přejít k vašemu samoobslužnému útoku na útok, kde jste službu zaplaveni nepřetržitými voláními vyčerpání prostředků, jako jsou paměť, vlákna a databáze. připojení, což způsobuje selhání nesouvisejících částí systému, které používají stejné prostředky.

V těchto situacích by bylo vhodnější, že operace selže okamžitě a pokusí se o vyvolání služby pouze v případě, že je pravděpodobně úspěšná.

[Vzor přerušení okruhu](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker) může aplikaci zabránit v opakovaném pokusu o provedení operace, která pravděpodobně selže. Monitoruje také aplikace s pravidelným zkušebním voláním, aby bylo možné zjistit, zda byla chyba vyřešena. Obrázek 6-5 ukazuje vzor přerušení okruhu v akci.

![Vzor přerušení okruhu v akci](./media/circuit-breaker-pattern.png)

**Obrázek 6-5**. Vzor přerušení okruhu v akci

Na předchozím obrázku byl do původního vzoru opakování přidán vzorek pro přerušení okruhu. Všimněte si, že po 10 neúspěšných žádostech se vypínače okruhu otevře a už neumožňuje volání služby. Hodnota CheckCircuit, nastavená na 30 sekund, určuje, jak často bude knihovna umožňovat, aby služba pokračovala v jednom požadavku. Pokud je toto volání úspěšné, okruh se zavře a služba bude znovu k dispozici pro provoz.

Mějte na paměti, že záměr vzorce pro dělení na okruhy se *liší* od vzoru opakování. Vzor opakování umožňuje aplikaci opakovat operaci v očekávaném případě, že bude úspěšná. Vzorek přerušení okruhu brání aplikaci v provedení operace, která pravděpodobně selže. Aplikace často *kombinuje* tyto dva vzorce pomocí vzoru opakování, aby vyvolala operaci pomocí přepínacího objektu okruhu. Logika opakování by však měla být citlivá na jakékoli výjimky vrácené koncovým objektem okruhu a pokusy o opakovaný pokus o zrušení, pokud je indikátorem okruhu indikováno, že chyba není přechodná.

Odolnost aplikace je potřeba ke zpracování problematických operací. Ale jde jenom o polovinu tohoto článku. V dalším kroku pokrýváme funkce odolnosti dostupné v cloudu Azure.

>[!div class="step-by-step"]
>[Předchozí](resiliency.md)
>[Další](infrastructure-resiliency-azure.md)
