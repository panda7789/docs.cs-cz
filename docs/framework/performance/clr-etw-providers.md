---
title: "Poskytovatelé CLR ETW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b76b3a1d4969a5ed81e5fa90afb06050b780804
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clr-etw-providers"></a>Poskytovatelé CLR ETW
Modul CLR (CLR) má dva poskytovatelé: Zprostředkovatel runtime a sekvence daneho zprostředkovatele.  
  
 Poskytovatel modulu runtime vyvolá událostí, v závislosti na tom, které jsou povolené klíčová slova (kategorie událostí). Například můžete shromažďovat události zavaděče povolení `LoaderKeyword` – klíčové slovo.  
  
 Sledování události systému Windows (ETW) událostí se protokolují do souboru, který má příponu ETL, který lze později po zpracovat v souborech hodnot oddělených čárkami (.csv) podle potřeby. Informace o tom, jak převést soubor .etl do souboru CSV naleznete v tématu [řízení protokolování rozhraní .NET Framework](../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="the-runtime-provider"></a>Poskytovatel modulu Runtime  
 Modul runtime se hlavní zprostředkovatel CLR ETW.  
  
 Poskytovatel modulu runtime CLR GUID je e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
 Příklady, jak protokolování a zobrazení CLR ETW – události pomocí běžných nástrojů, najdete v části [řízení protokolování rozhraní .NET Framework](../../../docs/framework/performance/controlling-logging.md).  
  
 Kromě používání klíčová slova, jako `LoaderKeyword`, možná budete muset povolit klíčová slova pro protokolování událostí, které mohou být vyvolány příliš často. `StartEnumerationKeyword` a `EndEnumerationKeyword` klíčová slova povolit tyto události a jsou shrnuty v [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).  
  
## <a name="the-rundown-provider"></a>Sekvence daneho zprostředkovatele  
 Sekvence daneho zprostředkovatele musí být zapnut pro určité speciální používá. Ale pro většinu uživatelů, měla by stačit runtime zprostředkovatele.  
  
 Sekvence daneho zprostředkovatel CLR GUID je A669021C-C450-4609-A035-5AF59AF4DF18.  
  
 Za normálních okolností je povoleno protokolování trasování událostí pro Windows předtím, než spustí proces a po ukončení procesu, je protokolování vypnuté. Ale pokud protokolování trasování událostí pro Windows zapnutý, při procesu provádí, je potřeba další informace o procesu. Například pro překlad symbol máte protokolování událostí, metoda pro metody, které již byly načteny před protokolování zapnutý.  
  
 `DCStart` a `DCEnd` události zaznamenat stav procesu, při shromažďování dat byl spuštění a zastavení. (Stav odkazuje na informace na vysoké úrovni, včetně metody, které již byly v běhu (JIT) zkompilovat a sestavení, které byly načteny.) Tyto dvě události může poskytnout informace o co bylo provedeno v procesu. například, které metody byly JIT-kompilovat, a tak dále.  
  
 Jenom události s `DC`, `DCStart`, `DCEnd`, nebo `DCInit` jejich názvy jsou vyvolány v rámci sekvence daneho zprostředkovatele. Kromě toho tyto události jsou vyvolány pouze v rámci sekvence daneho zprostředkovatele.  
  
 Kromě události – klíčové slovo filtry, sekvence daneho zprostředkovatel také podporuje `StartRundownKeyword` a `EndRundownKeyword` klíčová slova zajistit cílové filtrování.  
  
### <a name="start-rundown"></a>Spustit Rundown  
 Spuštění rundown se aktivuje, když je povoleno protokolování v rámci sekvence daneho zprostředkovatele s `StartRundownKeyword` – klíčové slovo. To způsobí, že `DCStart` událost, která má být vyvolána a zachytí stavu systému. Před zahájením výčtu `DCStartInit` událost se vyvolá. Na konci výčtu `DCStartComplete` událost se vyvolá, upozornit na řadič, který shromažďování dat ukončeno normálně.  
  
### <a name="end-rundown"></a>End Rundown  
 Rundown end se aktivuje, když je povoleno protokolování v rámci sekvence daneho zprostředkovatele s `EndRundownKeyword` – klíčové slovo. Profilace v procesu, který bude pokračovat v provádění sekvence daneho zastaví end. `DCEnd` Události zaznamenání stavu systému při vytváření profilu je zastavena.  
  
 Před zahájením výčtu `DCEndInit` událost se vyvolá. Na konci výčtu `DCEndComplete` událost se vyvolá oznámit příjemce, který shromažďování dat ukončeno normálně. Spuštění sekvence daneho a end rundown primárně pro spravované symbol řešení. Spuštění rundown může poskytnout informace o rozsah adres pro metody, které již byly kompilována před relace profilování byla spuštěna. End rundown může poskytnout informace o rozsah adres pro všechny metody, které byly kompilována při profilace je přibližně po zapnutí vypnout.  
  
 Pokud je zastavená relace profilování end rundown neprobíhá automaticky. Místo toho nástroj, který se snaží provést řešení spravované symbol má explicitně vyvolat relaci CLR sekvence daneho zprostředkovatele s `EndRundownKeyword` – klíčové slovo povoleno, těsně před profilace je zastavena.  
  
 I když rundown počáteční nebo koncové rundown může poskytnout informace o rozsahu adres metoda pro spravované symbol řešení, doporučujeme použít `EndRundownKeyword` – klíčové slovo (které zdroje `DCEnd` události) místo `StartRundownKeyword` – klíčové slovo (který poskytuje `DCStart` událostí). Pomocí `StartRundownKeyword` způsobí, že rundown provést během relace profilování, které by mohly narušit PROFILOVANÉHO scénář.  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>Shromažďování dat trasování událostí pro Windows pomocí modulu Runtime a sekvence daneho zprostředkovatelé  
 Následující příklad ukazuje, jak použít poskytovatele sekvence daneho CLR způsobem, který umožňuje řešení symbol spravovaných procesů s minimálním dopadem, bez ohledu na to, zda procesy začínat nebo končit uvnitř nebo mimo okno PROFILOVANÉHO.  
  
1.  Zapněte protokolování trasování událostí pro Windows pomocí zprostředkovatele runtime CLR:  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     Protokol se uloží do souboru clr1.etl.  
  
2.  Zastavit profilování při proces bude pokračovat v provádění, spusťte sekvence daneho zprostředkovatele, který má zaznamenat `DCEnd` události:  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     To umožňuje kolekce `DCEnd` události pro spuštění sekvence daneho relace. Pravděpodobně muset počkat 30 – 60 sekund pro všechny události, které se mají shromažďovat. Protokol se uloží do souboru clr1.et2.  
  
3.  Vypněte všechny profilace trasování událostí pro Windows:  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  Sloučení profilů vytvořit jeden soubor protokolu:  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     Soubor merged.etl bude obsahovat události z modulu runtime a relace sekvence daneho zprostředkovatele.  
  
 Nástroj můžete spustit kroky 2 a 3 (spuštění sekvence daneho relace a pak ukončení profilace) namísto okamžitě vypnutí profilace, když se uživatel požadavky profilace zastavení. Nástroj můžete spustit také krok 4.  
  
## <a name="see-also"></a>Viz také  
 [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
