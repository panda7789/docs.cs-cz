---
title: Vzory odolnosti aplikací
description: Architekt cloudových nativních aplikací .NET pro Azure | Vzory odolnosti aplikací
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: bb72e47704c833a2ce86f103a66b0414ce3a37ff
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614318"
---
# <a name="application-resiliency-patterns"></a>Vzory odolnosti aplikací

První linií obrany je odolnost aplikací.

I když můžete investovat do svého vlastního rozhraní odolného proti chybám, takové produkty už existují. [Polly](http://www.thepollyproject.org/) je komplexní odolnost proti chybám rozhraní .NET a knihovna pro plynulé zpracování chyb, která umožňuje vývojářům vyjádřit zásady odolnosti proti chybám v rámci Fluent a bezpečných vláken. Polly cílí na aplikace sestavené buď pomocí .NET Framework nebo .NET Core. Následující tabulka popisuje funkce odolné proti chybám, `policies` které jsou v knihovně Polly k dispozici. Je možné je použít individuálně nebo seskupit dohromady.

| Zásada | Prostředí |
| :-------- | :-------- |
| Zkusit znovu | Nakonfiguruje operace opakování u určených operací. |
| Circuit Breaker | Blokuje požadované operace v případě, že chyby překračují nakonfigurovanou prahovou hodnotu. |
| Časový limit | Míst omezuje dobu trvání, pro kterou volající může čekat na odpověď. |
| Bulkhead | Omezí akce na fond zdrojů s pevnou velikostí, aby nedocházelo k selhání volání z swamping prostředku. |
| Mezipaměť | Automaticky ukládá odpovědi. |
| Záložní volba | Definuje strukturované chování při selhání. |

Všimněte si, jak je uvedeno výše v předchozím obrázku zásady odolnosti platí pro zprávy s požadavkem, ať už přicházejí z externího klienta nebo back-endové služby. Cílem je kompenzovat žádost o službu, která může být v nedostupném případě. Tato krátkodobá přerušení obvykle společně využívají stavové kódy HTTP uvedené v následující tabulce.

| Stavový kód HTTP| Příčina |
| :-------- | :-------- |
| 404 | Nenalezeno |
| 408 | Časový limit žádosti |
| 429 | Příliš mnoho požadavků (pravděpodobně bylo omezeno) |
| 502 | Chybná brána |
| 503 | Služba není k dispozici |
| 504 | Časový limit brány |

Otázka: budete opakovat kód stavu HTTP 403 – zakázáno? Ne. V tomto případě systém pracuje správně, ale informuje volajícího, že nemá oprávnění k provedení požadované operace. Je nutné vzít v potaz pouze operace způsobené chybami.

Jak je to doporučeno v kapitole 1, vývojáři Microsoftu vytvářejí cloudové nativní aplikace, které by měly cílit na platformu .NET Core. Verze 2,1 zavedla knihovnu [HTTPClientFactory](https://www.stevejgordon.co.uk/introduction-to-httpclientfactory-aspnetcore) pro vytváření instancí klienta http pro interakci s prostředky založenými na adrese URL. Nahrazení původní třídy HTTPClient, třída Factory podporuje mnoho rozšířených funkcí, jedna z nich je [těsná integrace](../microservices/implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md) s knihovnou odolnosti Polly. Díky tomu můžete snadno definovat zásady odolnosti ve třídě spuštění aplikace, aby se mohla zpracovávat částečná selhání a problémy s připojením.

Teď se podíváme na vzory pokusů o opakování a okruhu.

### <a name="retry-pattern"></a>Model Opakování

V distribuovaném cloudovém nativním prostředí můžou volání služeb a cloudových prostředků selhat kvůli přechodným (krátkodobým) chybám, které se obvykle po krátké době vyřeší. Implementace strategie opakování pomáhá cloudovým nativním službám zmírnit tyto scénáře.

[Vzor opakování](https://docs.microsoft.com/azure/architecture/patterns/retry) umožňuje službě opakovat operaci neúspěšné žádosti a (konfigurovatelný) kolikrát s exponenciálně rostoucí čekací dobou. Obrázek 6-2 ukazuje opakování v akci.

![Vzor opakování v akci](./media/retry-pattern.png)

**Obrázek 6-2**. Vzor opakování v akci

Na předchozím obrázku byl pro operaci požadavku implementován vzor opakování. Je nakonfigurovaná tak, aby umožňovala až čtyři opakované pokusy, před selháním s intervalem omezení rychlosti (čekací doba) od 2 sekund, který exponenciálně zdvojnásobuje při každém dalším pokusu.

- První vyvolání se nezdařilo a vrátí stavový kód HTTP 500. Aplikace počká po dobu dvou sekund a zopakuje volání.
- Druhé vyvolání také nefunguje a vrátí stavový kód HTTP 500. Aplikace nyní zdvojnásobí omezení rychlosti interval na čtyři sekundy a zopakuje volání.
- Nakonec se třetí volání zdaří.
- V tomto scénáři by se pokus o operaci opakování při zdvojnásobení omezení rychlosti doby před selháním tohoto volání pokusil o čtyři opakované pokusy.
- Došlo k chybě 4. pokus o ověření se nezdařil, pro řádné zpracování problému se vyvolala záložní zásada.

Je důležité zvýšit omezení rychlosti období před opakovaným pokusem o volání, aby bylo možné čas služby samočinně opravovat. Osvědčeným postupem je implementovat exponenciálně rostoucí omezení rychlosti (zdvojnásobit periodu při každém opakování), aby se povolila adekvátní doba opravy.

## <a name="circuit-breaker-pattern"></a>Vzorek pro přerušení okruhu

I když vzor opakování může přispět k vyřazení žádosti entangled v částečném selhání, existují situace, kdy selhání může být způsobeno neočekávanými událostmi, které budou vyžadovat přeložení delší dobu. Tyto chyby můžou být různě závažné, od částečného výpadku připojení až po úplné selhání služby. V těchto situacích je bezúčelné pro aplikaci, aby se nepřetržitě opakovala operace, která není pravděpodobně úspěšná.

Kvůli horšímu provádění operací nepřetržitého opakování při opakovaném pokusu o nereagující službu vás může přejít na scénář útoku na nereagující službu, kde jste službu zaplavi pomocí nepřetržitých volání vyčerpání prostředků, jako jsou paměť, vlákna a databázová připojení, což způsobuje selhání nesouvisejících částí systému, které používají stejné prostředky.

V těchto situacích by bylo vhodnější, že operace selže okamžitě a pokusí se o vyvolání služby pouze v případě, že je pravděpodobně úspěšná.

[Vzor přerušení okruhu](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker) může aplikaci zabránit v opakovaném pokusu o provedení operace, která pravděpodobně selže. Po předem definovaném počtu neúspěšných volání blokuje veškerý provoz do služby. Pravidelně to umožní zkušebnímu volání zjistit, jestli se chyba vyřešila. Obrázek 6-3 ukazuje vzor přerušení okruhu v akci.

![Vzor přerušení okruhu v akci](./media/circuit-breaker-pattern.png)

**Obrázek 6-3**. Vzor přerušení okruhu v akci

Na předchozím obrázku byl do původního vzoru opakování přidán vzorek pro přerušení okruhu. Všimněte si, že po 100 neúspěšných žádostech se vypínače okruhu otevře a už neumožňuje volání služby. Hodnota CheckCircuit, nastavená na 30 sekund, určuje, jak často bude knihovna umožňovat, aby služba pokračovala v jednom požadavku. Pokud je toto volání úspěšné, okruh se zavře a služba bude znovu k dispozici pro provoz.

Mějte na paměti, že záměr vzorce pro dělení na okruhy se *liší* od vzoru opakování. Vzor opakování umožňuje aplikaci opakovat operaci v očekávaném případě, že bude úspěšná. Vzorek přerušení okruhu brání aplikaci v provedení operace, která pravděpodobně selže. Aplikace obvykle *zkombinuje* tyto dva vzory pomocí vzoru opakování pro vyvolání operace prostřednictvím přerušení okruhu.

## <a name="testing-for-resiliency"></a>Testování odolnosti proti chybám

Testování odolnosti proti chybám nelze vždy provést stejným způsobem, jakým testujete funkčnost aplikace (spuštěním testů jednotek, integračních testů atd.). Místo toho musíte otestovat, jak se bude celá úloha v celém rozsahu chovat, když dojde k selhání, třeba i přerušovanému. Například: vložení chyb na základě selhání procesů, certifikátů s vypršenou platností, nedostupnost závislých služeb atd. Pro takové testování chaos lze použít rozhraní, jako je [chaos-opice](https://github.com/Netflix/chaosmonkey) .

Odolnost aplikace je potřeba ke zpracování problematických operací. Ale jde jenom o polovinu tohoto článku. V dalším kroku pokrýváme funkce odolnosti dostupné v cloudu Azure.

>[!div class="step-by-step"]
>[Předchozí](resiliency.md) 
> [Další](infrastructure-resiliency-azure.md)
