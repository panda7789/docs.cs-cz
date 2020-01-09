---
title: Poskytovatelé CLR ETW
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
ms.openlocfilehash: dbdd4ad862ae300c330dc56a82fcd65b866855b6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716186"
---
# <a name="clr-etw-providers"></a>Poskytovatelé CLR ETW
Modul CLR (Common Language Runtime) má dva zprostředkovatele: poskytovatele modulu runtime a poskytovatele doběhu.  
  
 Zprostředkovatel modulu runtime vyvolává události v závislosti na tom, která klíčová slova (kategorie událostí) jsou povolena. Například můžete shromáždit události zavaděče povolením klíčového slova `LoaderKeyword`.  
  
 Události trasování událostí pro Windows (ETW) jsou protokolovány do souboru s příponou. ETL, která může být později zpracována v souborech hodnot oddělených čárkou (. csv) podle potřeby. Informace o tom, jak převést soubor. ETL na soubor. csv, najdete v tématu [řízení .NET Framework protokolování](controlling-logging.md).  
  
## <a name="the-runtime-provider"></a>Zprostředkovatel modulu runtime  
 Poskytovatel modulu runtime je hlavním zprostředkovatelem modulu CLR ETW.  
  
 Identifikátor GUID zprostředkovatele modulu runtime CLR je e13c0d23-CCBC-4e12-931B-d9cc2eee27e4.  
  
 Příklady, jak pomocí běžně dostupných nástrojů protokolovat a zobrazovat události CLR ETW, najdete v tématu [řízení .NET Framework protokolování](controlling-logging.md).  
  
 Kromě používání klíčových slov, jako je například `LoaderKeyword`, možná budete muset povolit klíčová slova pro protokolování událostí, které mohou být vyvolány příliš často. `StartEnumerationKeyword` a klíčová slova `EndEnumerationKeyword` tyto události umožňují a jsou shrnuty v [klíčových slovech a klíčích modulu CLR ETW](clr-etw-keywords-and-levels.md).  
  
## <a name="the-rundown-provider"></a>Poskytovatel doběhu  
 Pro určité účely zvláštního použití musí být poskytovatel doběhu zapnutý. Nicméně pro většinu uživatelů by měl stačit poskytovatel modulu runtime.  
  
 Identifikátor GUID zprostředkovatele doběhu CLR je A669021C-C450-4609-A035-5AF59AF4DF18.  
  
 V normálním případě je protokolování ETW povoleno před spuštěním procesu a protokolování je po ukončení procesu vypnuté. Pokud je však protokolování ETW při provádění procesu zapnuté, pro tento proces jsou potřeba další informace. Například pro rozlišení symbolů musíte protokolovat události metody pro metody, které již byly načteny před zapnutím protokolování.  
  
 Události `DCStart` a `DCEnd` zachytí stav procesu při spuštění a zastavení shromažďování dat. (Stav odkazuje na informace na vysoké úrovni, včetně metod, které již byly zkompilovány JIT (just-in-time) a sestavení, která byla načtena.) Tyto dvě události mohou poskytnout informace o tom, co se v procesu již stalo. například které metody byly kompilovány JIT a tak dále.  
  
 V rámci poskytovatele doběhu jsou vyvolány pouze události, které se `DC`, `DCStart`, `DCEnd`nebo `DCInit` v jejich názvech. Kromě toho jsou tyto události vyvolány pouze pod poskytovatelem doběhu.  
  
 Kromě filtrů klíčového slova události poskytovatel doběhu také podporuje klíčová slova `StartRundownKeyword` a `EndRundownKeyword` k zajištění cíleného filtrování.  
  
### <a name="start-rundown"></a>Spustit doběhu  
 Pokud je povoleno protokolování pod poskytovatelem doběhu s klíčovým slovem `StartRundownKeyword`, aktivuje se spouštěcí doběhu. Tím dojde k vyvolání události `DCStart` a zachycení stavu systému. Před začátkem výčtu je vyvolána událost `DCStartInit`. Na konci výčtu je vyvolána událost `DCStartComplete`, která upozorní kontrolér na to, že sběr dat byl ukončen normálně.  
  
### <a name="end-rundown"></a>Konec doběhu  
 Pokud je povoleno protokolování pod poskytovatelem doběhu, je aktivována koncová doběhu s klíčovým slovem `EndRundownKeyword`. Konec doběhu zastaví profilování u procesu, který pokračuje v provádění. `DCEnd` události zachytí stav systému při zastavení profilace.  
  
 Před začátkem výčtu je vyvolána událost `DCEndInit`. Na konci výčtu je vyvolána událost `DCEndComplete`, aby příjemce upozornil na to, že sběr dat byl ukončen normálně. Spuštění doběhu a end doběhu se primárně používá pro spravované rozlišení symbolů. Spustit doběhu může poskytnout informace o rozsahu adres pro metody, které již byly kompilovány JIT před spuštěním relace profilování. Koncová doběhu může poskytnout informace o rozsahu adres pro všechny metody, které byly kompilovány JIT, když se profilování vypíná.  
  
 K ukončení doběhu dojde automaticky při zastavení relace profilování. Místo toho nástroj, který se pokouší provést rozlišení spravovaného symbolu, musí explicitně vyvolat relaci poskytovatele CLR doběhu s povoleným klíčovým slovem `EndRundownKeyword`, těsně před zastavením profilace.  
  
 I když buď spustit doběhu nebo End doběhu může poskytnout informace o rozsahu adres pro spravované řešení, doporučujeme použít klíčové slovo `EndRundownKeyword` (které poskytuje `DCEnd` události) místo klíčového slova `StartRundownKeyword` (které poskytuje `DCStart` události). Použití `StartRundownKeyword` způsobí, že doběhu proběhne během relace profilování, což může narušit scénář profilace.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Shromažďování dat ETW pomocí zprostředkovatelů runtime a doběhu  
 Následující příklad ukazuje, jak použít poskytovatele CLR doběhu způsobem, který umožňuje rozlišení symbolů spravovaných procesů s minimálním dopadem, bez ohledu na to, zda procesy začínají nebo končí uvnitř nebo vně profilace okna.  
  
1. Zapnout protokolování ETW pomocí zprostředkovatele modulu CLR Runtime:  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     Protokol bude uložen do souboru souboru clr1. ETL.  
  
2. Chcete-li zastavit profilaci, když proces pokračuje v provádění, spusťte poskytovatele doběhu a zaznamenejte události `DCEnd`:  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     To umožňuje kolekci událostí `DCEnd` spustit relaci doběhu. Pro shromáždění všech událostí možná budete muset počkat 30 až 60 sekund. Protokol bude uložen do souboru souboru clr1. ET2.  
  
3. Vypnout všechny profily trasování událostí pro Windows:  
  
    ```console
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4. Sloučením profilů vytvořte jeden soubor protokolu:  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     Sloučený soubor. ETL bude obsahovat události z relací zprostředkovatelů runtime a doběhu.  
  
 Nástroj může spustit kroky 2 a 3 (spuštění relace doběhu a následná ukončení profilace) místo okamžitého vypnutí profilování, když uživatel požaduje, aby bylo profilování zastaveno. Nástroj může také provádět krok 4.  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](etw-events-in-the-common-language-runtime.md)
