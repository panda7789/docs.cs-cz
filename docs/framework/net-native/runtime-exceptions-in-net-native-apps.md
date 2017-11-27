---
title: "Výjimky za běhu v nativní aplikace .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d4f5787faa2fdf5f5450d8ddce285919a658645
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-exceptions-in-net-native-apps"></a>Výjimky za běhu v nativní aplikace .NET
Je důležité k testování verze sestavení vaší aplikace pro univerzální platformu Windows na jejich cílových platforem, protože konfigurace debug a release jsou úplně jiné. Ve výchozím nastavení konfiguraci ladění používá na .NET Core runtime pro kompilaci aplikace, ale konfigurace verze používá .NET Native pro kompilaci vaší aplikace do nativního kódu.  
  
> [!IMPORTANT]
>  Informace o práci s [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky, které mohou stane se při testování verze aplikace, najdete v části "krok 4: vyřešit ručně chybí metadata: v [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md) tématu, a také [reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) a [ Odkaz na soubor konfigurace modulu runtime direktivy (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Ladění a sestavení pro vydání  
 Při ladění sestavení provede proti na .NET Core runtime, nebyl kompilovaná nativního kódu. Díky tomu všechny služby normálně poskytované modul runtime, která je k dispozici pro vaši aplikaci.  
  
 Na druhé straně sestavení pro vydání zkompiluje do nativního kódu pro jeho cílových platforem, odebere většina závislostí na externí moduly runtime a knihovny a výraznou optimalizuje kód pro maximální výkon.  
  
 Když ladíte verze sestavení, které jsou kompilovaná pomocí .NET Native:  
  
-   Použijete .NET nativní modul ladění, který se liší od normální .NET nástroje pro ladění.  
  
-   Velikost vaší spustitelný soubor se snižuje co nejvíc. Jedním ze způsobů, .NET Native snižuje velikost spustitelný soubor je výrazně ořezávání zprávy o výjimkách runtime, téma větší podrobněji v [zprávy o výjimkách Runtime](#Messages) části.  
  
-   Váš kód je výraznou optimalizovaná. To znamená, že vložené se používá, pokud je to možné. (Vložené přesune kód z externí rutiny do volání rutiny.)   Skutečnost, že .NET Native poskytuje specializované runtime a implementuje ovlivní smělého vložené zásobníku volání, která se zobrazuje při ladění.  Další informace najdete v tématu [zásobník volání modulu Runtime](#CallStack) části.  
  
> [!NOTE]
>  Můžete řídit, jestli buildy debug a release jsou kompilovaná s .NET Native řetězu nástroj zaškrtnutí **kompilovat s .NET Native řetězu nástroj** pole.   Upozorňujeme však, že Windows Store vždy zkompilovat produkční verzi vaší aplikace pomocí .NET Native řetězu nástroj.  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a>Zprávy o výjimkách modulu runtime  
 Chcete-li minimalizovat velikost spustitelný soubor aplikace, .NET Native nezahrnuje celého textu zprávy výjimek. V důsledku toho nemusí runtime výjimky vydané v sestavení pro vydání zobrazit celý text zprávy výjimek. Místo toho může být podřetězce spolu s odkazem na použijte další informace. Například může zobrazit informace o výjimce jako:  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Pokud potřebujete zpráva o výjimce dokončení, spusťte ladění sestavení. Předchozí informace o výjimce ze sestavení pro vydání může například vypadat takto v sestavení ladicí verze:  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a>Zásobník volání modulu runtime  
 Z důvodu optimalizace vložené a dalších zásobníku volání zobrazí aplikací zkompilují řetězu .NET Native nástroj nemusí vám pomohou pro jednoznačnou identifikaci cestu k výjimku modulu runtime.  
  
 Pokud chcete získat úplné zásobníku, spusťte ladění sestavení místo.  
  
## <a name="see-also"></a>Viz také  
 [Ladění rozhraní .NET nativní univerzálních aplikací pro Windows](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx)  
 [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)
