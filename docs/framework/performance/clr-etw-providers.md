---
title: Poskytovatelé CLR ETW
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 639ebe1552fd3950bd77acd7b5730b0d3bdb150f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302618"
---
# <a name="clr-etw-providers"></a>Poskytovatelé CLR ETW
Modul CLR (CLR) má dva zprostředkovatele: zprostředkovatele běhového prostředí a zprostředkovatele doběhu.  
  
 Zprostředkovatel modulu runtime vyvolává události, v závislosti na tom, které jsou povolené klíčová slova (kategorie události). Například můžete shromažďovat události načítání povolením `LoaderKeyword` – klíčové slovo.  
  
 Událost sledování pro Windows (ETW) jsou zaznamenány do souboru s příponou ETL, který lze později zpracovat do souborů hodnot oddělených čárkami (CSV), podle potřeby. Informace o převodu souborů ETL do souboru CSV najdete v tématu [řízení protokolování rozhraní .NET Framework](../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="the-runtime-provider"></a>Zprostředkovatel běhového prostředí  
 Zprostředkovatel běhového prostředí je hlavním zprostředkovatelem modulu CLR ETW.  
  
 Identifikátor GUID zprostředkovatele CLR runtime je e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
 Příklady protokolování a zobrazení událostí CLR ETW pomocí běžných nástrojů, naleznete v tématu [řízení protokolování rozhraní .NET Framework](../../../docs/framework/performance/controlling-logging.md).  
  
 Kromě použití klíčových slov, jako `LoaderKeyword`, možná budete muset povolit klíčová slova pro protokolování událostí, které mohou být vyvolány příliš často. `StartEnumerationKeyword` a `EndEnumerationKeyword` klíčová slova povolují tyto události a jsou shrnuta v [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).  
  
## <a name="the-rundown-provider"></a>Zprostředkovatel doběhu  
 Zprostředkovatel doběhu musí být zapnuta pro některé zvláštní účely použití. Pro většinu uživatelů však měl postačit zprostředkovatel běhového prostředí.  
  
 Identifikátor GUID zprostředkovatele doběhu modulu CLR je A669021C-C450-4609-A035-5AF59AF4DF18.  
  
 Za normálních okolností je protokolování ETW povoleno před spustí proces a po ukončení procesu, je protokolování vypnuté. Nicméně pokud protokolování trasování událostí pro Windows je zapnuto při provádění procesu, je potřeba další informace o procesu. Například pro rozlišení symbolů máte zaznamenat události metod pro metody, které již byly zavedeny před zapnutím protokolování.  
  
 `DCStart` a `DCEnd` události zachycují stav procesu při shromažďování dat bylo spuštění a zastavení. (Stav odkazuje na informace na vysoké úrovni, včetně metod, které již byly just-in-time (JIT) zkompilována a sestavení, která byla načtena.) Tyto dvě události mohou poskytnout informace o co se stalo již v procesu. například které metody byly zkompilovány JIT, a tak dále.  
  
 Pouze události, jejichž `DC`, `DCStart`, `DCEnd`, nebo `DCInit` v názvu jsou vyvolány skrze zprostředkovatele doběhu. Kromě toho tyto události jsou vyvolány pouze skrze zprostředkovatele doběhu.  
  
 Kromě filtrů klíčových slov událostí zprostředkovatele doběhu také podporuje `StartRundownKeyword` a `EndRundownKeyword` klíčová slova k poskytování cílení filtrování.  
  
### <a name="start-rundown"></a>Začátek doběhu  
 Začátek doběhu je vyvolán, pokud je povoleno protokolování zprostředkovatele doběhu pomocí `StartRundownKeyword` – klíčové slovo. To způsobí, že `DCStart` událost vyvolána a zachycen stav systému. Před zahájením výčtu `DCStartInit` událost se vyvolá. Na konci výčtu `DCStartComplete` událost je vyvolávána s cílem upozornit kontroler, který sběr dat byl korektně ukončen.  
  
### <a name="end-rundown"></a>Konec doběhu  
 Konec doběhu se aktivuje, když je povoleno protokolování zprostředkovatele doběhu pomocí `EndRundownKeyword` – klíčové slovo. Konec doběhu zastaví profilování procesu, který pokračuje v provádění. `DCEnd` Události zachycují stav systému, když je profilování zastaveno.  
  
 Před zahájením výčtu `DCEndInit` událost se vyvolá. Na konci výčtu `DCEndComplete` událost je vyvolávána s cílem upozornit, že sběr dat byl korektně ukončen. Začátek doběhu a konec doběhu jsou primárně určené pro rozlišení spravovaných symbolů. Začátek doběhu může poskytnout informace o metodách, které již byly zkompilovány JIT před spuštěním relace profilování se rozsahu adres. Konec doběhu může poskytnout informace o rozsahu adres pro všechny metody, které byly zkompilovány JIT profilace se vypne.  
  
 Konec doběhu neprobíhá automaticky při zastavení relace profilování. Místo toho nástroj, který se snaží provést rozlišení spravovaných symbolů musí explicitně vyvolat relaci zprostředkovatele doběhu modulu CLR s `EndRundownKeyword` – klíčové slovo povolena, pouze předtím, než je profilování zastaveno.  
  
 Přestože začátek doběhu a konec doběhu může poskytnout informace o rozsahu adres metody pro rozlišení spravovaných symbolů, doporučujeme použít `EndRundownKeyword` – klíčové slovo (které poskytuje `DCEnd` události) místo `StartRundownKeyword` – klíčové slovo (který poskytuje `DCStart` události). Pomocí `StartRundownKeyword` způsobí spuštění doběhu během relace profilování, což může narušit profilovaný scénář.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Shromažďování dat trasování událostí pro Windows pomocí modulu Runtime a zprostředkovatele doběhu  
 Následující příklad ukazuje použití zprostředkovatele doběhu modulu CLR způsobem, který umožňuje rozlišení symbolů pro spravované procesy s minimálním dopadem, bez ohledu na to, zda procesy začínají nebo končí uvnitř nebo vně profilovacího okna.  
  
1. Zapnutí protokolování událostí ETW pomocí zprostředkovatele modulu CLR runtime:  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     Protokol bude uložen do souboru clr1.etl.  
  
2. K zastavení profilování, zatímco proces pokračuje v provádění, spustit zprostředkovatele doběhu zachycení `DCEnd` události:  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     To umožňuje shromažďování `DCEnd` události spuštění relace doběhu. Budete muset počkat 30 – 60 sekund pro všechny události, které se mají shromažďovat. Protokol bude uložen do souboru clr1.et2.  
  
3. Vypnutí všech profilování ETW:  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4. Je třeba sloučit profily pro vytvoření jednoho souboru protokolu:  
  
    ```  
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     Soubor merged.etl bude obsahovat události z modulu runtime a relace skrze zprostředkovatele doběhu.  
  
 Nástroj může spustit kroky 2 a 3 (spuštění relace doběhu a potom ukončení profilování) místo okamžitého vypnutí profilování, když uživatel žádostí, aby bylo profilování zastaveno. Nástroj může také spustit krok 4.  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
