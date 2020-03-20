---
title: Poskytovatelé CLR ETW
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
ms.openlocfilehash: 33ef7491c2bffeda4ef737ed8f826cdfbfbb119d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400076"
---
# <a name="clr-etw-providers"></a>Poskytovatelé CLR ETW
Běžný jazyk runtime (CLR) má dva zprostředkovatele: zprostředkovatele runtime a zprostředkovatele rundown.  
  
 Zprostředkovatel runtime vyvolává události v závislosti na tom, která klíčová slova (kategorie událostí) jsou povolena. Můžete například shromažďovat události zavaděče povolením klíčového `LoaderKeyword` slova.  
  
 Události trasování událostí pro Windows (ETW) jsou zaznamenány do souboru, který má příponu .etl, která může být později podle potřeby post-processována v souborech s hodnotou oddělenou čárkou (.csv). Informace o převodu souboru .etl na soubor CSV naleznete [v tématu Controlling .NET Framework Logging](controlling-logging.md).  
  
## <a name="the-runtime-provider"></a>Zprostředkovatel runtime  
 Zprostředkovatel runtime je hlavním poskytovatelem CLR ETW.  
  
 Identifikátor GUID zprostředkovatele runtime CLR je e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
 Příklady protokolování a zobrazení událostí CLR ETW pomocí běžně dostupných nástrojů naleznete [v tématu Controlling .NET Framework Logging](controlling-logging.md).  
  
 Kromě použití klíčových slov, jako `LoaderKeyword`je například , bude pravděpodobně muset povolit klíčová slova pro protokolování událostí, které mohou být vyvolány příliš často. Klíčová `StartEnumerationKeyword` `EndEnumerationKeyword` slova a umožňují tyto události a jsou shrnuty v [CLR ETW klíčová slova a úrovně](clr-etw-keywords-and-levels.md).  
  
## <a name="the-rundown-provider"></a>Zprostředkovatel rundownu  
 Zprostředkovatel rundown musí být zapnutý pro určité speciální použití. Pro většinu uživatelů by však měl stačit zprostředkovatel runtime.  
  
 Identifikátor GUID zprostředkovatele rundown u CLR je A669021C-C450-4609-A035-5AF59AF4DF18.  
  
 Za normálních okolností protokolování ETW je povolena před spuštěním procesu a protokolování je vypnuto po ukončení procesu. Pokud je však protokolování ETW zapnuto během provádění procesu, jsou potřebné další informace o procesu. Například pro rozlišení symbolů je třeba protokolovat události metody pro metody, které již byly načteny před zapnutím protokolování.  
  
 A `DCStart` `DCEnd` události zachycují stav procesu při spuštění a zastavení shromažďování dat. (State odkazuje na informace na vysoké úrovni, včetně metod, které byly již just-in-time (JIT) zkompilovány a sestavení, které byly načteny.) Tyto dvě události mohou poskytnout informace o tom, co se již v tomto procesu stalo; například, které metody byly zkompilovány JIT a tak dále.  
  
 Pouze události `DC`s `DCStart` `DCEnd`, `DCInit` , , nebo v jejich názvech jsou vyvolány v rámci zprostředkovatele rundown. Kromě toho tyto události jsou vyvolány pouze v rámci zprostředkovatele rundown.  
  
 Kromě filtrů klíčových slov události podporuje zprostředkovatel `StartRundownKeyword` `EndRundownKeyword` rundown také klíčová slova a poskytuje cílené filtrování.  
  
### <a name="start-rundown"></a>Spustit rundown  
 Spuštění rundown se aktivuje při protokolování pod zprostředkovatele rundown je povoleno s klíčovým slovem. `StartRundownKeyword` To způsobí, že `DCStart` událost, která má být vyvolána a zachycuje stav systému. Před zahájením výčtu je `DCStartInit` vyvolána událost. Na konci výčtu `DCStartComplete` je vyvolána událost oznámit správce, že shromažďování dat ukončeno normálně.  
  
### <a name="end-rundown"></a>Konec rundownu  
 Konec rundown se aktivuje při protokolování pod zprostředkovatele rundown je povoleno s klíčovým slovem. `EndRundownKeyword` Konec rundown zastaví profilování na proces, který pokračuje v provádění. Události `DCEnd` zachycují stav systému při zastavení profilování.  
  
 Před zahájením výčtu je `DCEndInit` vyvolána událost. Na konci výčtu `DCEndComplete` je vyvolána událost oznámit spotřebiteli, že shromažďování dat ukončeno normálně. Spustit rundown a end rundown se používají především pro spravované rozlišení symbolů. Spuštění rundown můžete poskytnout informace o rozsahu adres pro metody, které byly již JIT kompilovány před zahájením relace profilování. End rundown může poskytnout informace o rozsahu adres pro všechny metody, které byly zkompilovány JIT při profilování se chystá vypnout.  
  
 Konec rundown se nestane automaticky při profilování relace je zastavena. Místo toho nástroj, který se snaží provést spravované rozlišení symbolu má explicitně vyvolat relaci zprostředkovatele clr s povoleným `EndRundownKeyword` klíčovým slovem, těsně před profilování je zastavena.  
  
 I když buď start rundown nebo end rundown může poskytnout informace o `EndRundownKeyword` rozsahu adresy metody `DCEnd` pro spravované rozlišení symbolů, doporučujeme použít klíčové slovo (které dodává události) namísto `StartRundownKeyword` klíčového slova (které poskytuje `DCStart` události). Použití `StartRundownKeyword` způsobí, že rundown dojít během relace profilování, které mohou narušit profilovaný scénář.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Shromažďování dat ETW pomocí runtime a zprostředkovatelů rundownu  
 Následující příklad ukazuje, jak používat zprostředkovatele rundown CLR způsobem, který umožňuje rozlišení symbolů spravovaných procesů s minimálním dopadem, bez ohledu na to, zda procesy začínají nebo končí uvnitř nebo vně profilovaného okna.  
  
1. Zapněte protokolování ETW pomocí zprostředkovatele runtime CLR:  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl
    ```  
  
     Protokol bude uložen do souboru clr1.etl.  
  
2. Chcete-li zastavit profilování, zatímco proces pokračuje v provádění, spusťte zprostředkovatele rundown zachytit `DCEnd` události:  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl
    ```  
  
     To umožňuje shromažďování `DCEnd` událostí spustit relaci rundown. Možná budete muset počkat 30 až 60 sekund pro všechny události, které mají být shromažďovány. Protokol bude uložen do souboru clr1.et2.  
  
3. Vypněte veškeré profilování ETW:  
  
    ```console
    xperf -stop clrRundown
    xperf -stop clr  
    ```  
  
4. Sloučit profily a vytvořit jeden soubor protokolu:  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     Soubor merged.etl bude obsahovat události z runtime a rundown zprostředkovatele relací.  
  
 Nástroj může provést kroky 2 a 3 (spuštění rundown ové relace a následné ukončení profilování) namísto okamžitého vypnutí profilování, když uživatel požádá o zastavení profilování. Nástroj může také provést krok 4.  
  
## <a name="see-also"></a>Viz také

- [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](etw-events-in-the-common-language-runtime.md)
