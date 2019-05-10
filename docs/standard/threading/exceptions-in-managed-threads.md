---
title: Výjimky ve spravovaných vláknech
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43037f897dfb591572a62a9bb3cccf9170d1f5fe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645013"
---
# <a name="exceptions-in-managed-threads"></a>Výjimky ve spravovaných vláknech
Od verze rozhraní .NET Framework verze 2.0, modul common language runtime umožňuje nejvíce neošetřené výjimky ve vláknech přirozeně pokračovat. Ve většině případů to znamená, že neošetřené výjimky způsobí ukončení aplikace.  
  
> [!NOTE]
>  Jedná se o významnou změnu z rozhraní .NET Framework verze 1.0 a 1.1, které poskytují backstop pro velký počet neošetřených výjimek, například neošetřených výjimek ve vláknu fondu vláken. Zobrazit [změnit z předchozích verzí](#ChangeFromPreviousVersions) dále v tomto tématu.  
  
 Modul common language runtime poskytuje backstop pro určité neošetřené výjimky, které se používají pro řízení toku programu:  
  
- A <xref:System.Threading.ThreadAbortException> je vyvolána ve vlákně, protože <xref:System.Threading.Thread.Abort%2A> byla volána.  
  
- <xref:System.AppDomainUnloadedException> Je vyvolána ve vlákně, protože probíhá uvolnění domény aplikace 00Z vlákno provádění.  
  
- Modul common language runtime nebo hostitelský proces ukončí vláknu vyvoláním vnitřní výjimky.  
  
 Pokud jsou některé z těchto výjimek není ošetřená v vlákna vytvořená modulem common language runtime, výjimka ukončí vlákno, ale modul common language runtime nepovoluje výjimky, abyste mohli pokračovat.  
  
 Je-li tyto výjimky nejsou zpracovány v hlavním vlákně, nebo vlákna, která zadaný modul runtime z nespravovaného kódu, odeslaných za normálních okolností výsledkem ukončení aplikace.  
  
> [!NOTE]
>  Je možné pro modul runtime vyvolá neošetřenou výjimku před spravovaný kód dostala příležitost k instalaci obslužné rutiny výjimky. I když spravovaného kódu dříve žádné příležitost dobře se zpracovat výjimku, může pokračovat přirozeně výjimku.  
  
## <a name="exposing-threading-problems-during-development"></a>Vystavení dělení na vlákna problémy při vývoji  
 Pokud vlákna mají povoleno provést tiše, bez ukončení aplikace, může pokračovat nezjištěné po programovací vážným problémům. Toto je konkrétního problému pro služby a další aplikace, které běží po delší dobu. Jak vlákna selže, je poškozený postupně stav programu. Může se snížit výkon aplikace nebo může být zablokování aplikace.  
  
 Povolení neošetřené výjimky v vlákna přirozeně, pokračovat až do doby ukončení programu, operační systém poskytuje tyto problémy během vývoje a testování. Zprávy o chybách program ukončení podpory ladění.  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a>Změnit z předchozí verze  
 Nejvýznamnější změnou se vztahují na spravovaná vlákna. Modul common language runtime v rozhraní .NET Framework verze 1.0 a 1.1, poskytuje backstop neošetřené výjimky v následujících situacích:  
  
- Není k dispozici i neošetřená výjimka ve vláknu fondu vláken. Pokud úloha vyvolá výjimku, která nezpracovává, modul runtime vytiskne trasování zásobníku výjimky do konzoly a potom vrátí vláknu fondu vláken.  
  
- Neexistuje žádná taková věc jako neošetřené výjimce ve vlákně vytvořené pomocí <xref:System.Threading.Thread.Start%2A> metodu <xref:System.Threading.Thread> třídy. Pokud kód spuštěný na těchto vlákno vyvolá výjimku, která nezpracovává, modul runtime vytiskne trasování zásobníku výjimky do konzoly a řádně ukončí vlákno.  
  
- Není k dispozici i neošetřené výjimky na finalizační podproces. Pokud finalizační metoda vyvolá výjimku, která nezpracovává, modul runtime vytiskne trasování zásobníku výjimky do konzoly a pak umožní vlákna finalizační metody obnovte spuštěnou finalizační metody.  
  
 Popředí nebo pozadí stav spravovaného vlákna nemá vliv na toto chování.  
  
 Pro neošetřené výjimky ve vláknech pocházející z nespravovaného kódu je složitější rozdíl. Dialogové okno Připojit JIT runtime brání dialogové okno operačního systému pro výjimky pro spravované nebo nativní na vláknech, které se mají předat prostřednictvím nativního kódu. Proces skončí ve všech případech.  
  
### <a name="migrating-code"></a>Migrace kódu  
 Obecně platí tato změna bude vystavovat dříve nerozpoznaný programovací problémy tak, aby je. V některých případech však programátoři trvalo výhod backstop modulu runtime, například ukončení vlákna. V závislosti na situaci že zvažte jednu z následujících strategií migrace:  
  
- Změny struktury kód, aby vlákno ukončí bez výpadku po přijetí signálu.  
  
- Použití <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metodu pro přerušení vlákna.  
  
- Pokud vlákno musí být zastaven, ukončení procesu mohli pokračovat, ujistěte se, vlákna vlákna na pozadí tak, aby je automaticky ukončeno na ukončení procesu.  
  
 Ve všech případech postupujte podle strategie pokyny návrhu pro výjimky. Zobrazit [pokyny návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md).  
  
### <a name="application-compatibility-flag"></a>Příznak kompatibility aplikace  
 Jako dočasné kompatibility opatření, můžete správci umístit příznak kompatibility v `<runtime>` oddílu konfiguračního souboru aplikace. To způsobí, že modul common language runtime se vrátit k chování verze 1.0 a 1.1.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Přepsání hostitele  
 V rozhraní .NET Framework verze 2.0, můžete použít nespravovaný hostitel [iclrpolicymanager –](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) rozhraní v rozhraní API pro hostování výchozí hodnotu přepsat neošetřené výjimky zásad modul common language runtime. [Iclrpolicymanager::setunhandledexceptionpolicy –](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) funkce se používá k nastavení zásad pro neošetřené výjimky.  
  
## <a name="see-also"></a>Viz také:

- [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)
