---
title: Výjimky za běhu v nativních aplikací .NET
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 3132e2c9502c91cbfa0b120f664fd0c6f99a2663
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128147"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>Výjimky za běhu v nativních aplikací .NET
Je důležité otestovat buildy vydání vaší Univerzální platforma Windows aplikace na svých cílových platformách, protože konfigurace ladění a vydání jsou zcela odlišné. Ve výchozím nastavení používá konfigurace ladění modul runtime .NET Core ke kompilaci vaší aplikace, ale konfigurace vydané verze používá .NET Native ke kompilaci vaší aplikace do nativního kódu.  
  
> [!IMPORTANT]
> Informace o tom, jak řešit výjimky [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , se kterými se můžete setkat při testování verzí verze vaší aplikace, najdete v části Krok 4: Ruční řešení chybějících metadat: v tématu [Začínáme](getting-started-with-net-native.md) a také v odkazech na konfigurační soubor direktivy [reflexe a .NET Native](reflection-and-net-native.md) a [runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Sestavení ladění a vydaných verzí  
 Když se sestavení ladění provede proti modulu runtime .NET Core, není zkompilováno do nativního kódu. Díky tomu jsou všechny služby běžně poskytované modulem runtime dostupným pro vaši aplikaci.  
  
 Na druhé straně sestavení pro vydání se zkompiluje do nativního kódu pro své cílové platformy, odebírá většinu závislostí na externích modulech runtime a knihoven a silně optimalizuje kód pro maximální výkon.  
  
 Při ladění sestavení vydaných verzí, která jsou kompilována pomocí .NET Native:  
  
- Použijete modul .NET Native ladění, který se liší od normálních ladicích nástrojů .NET.  
  
- Velikost spustitelného souboru se zmenší co nejvíce. Jedním z způsobů, jak .NET Native zmenší velikost spustitelného souboru, je tím, že významně vystřihují zprávy o výjimkách modulu runtime, téma podrobněji popsané v části [zprávy o výjimkách modulu runtime](#Messages) .  
  
- Váš kód je intenzivně optimalizovaný. To znamená, že pokud je to možné, používá se vkládání. (Vkládání kódu přesouvá kód z externích rutin do volající rutiny.)   Fakt, že .NET Native poskytuje specializované prostředí runtime a implementuje agresivní vkládání, má vliv na zásobník volání, který se zobrazí při ladění.  Další informace naleznete v části [zásobník volání modulu runtime](#CallStack) .  
  
> [!NOTE]
> Můžete určit, zda jsou sestavení ladění a vydání kompilována pomocí .NET Nativeho řetězu nástroje zaškrtnutím nebo zrušením zaškrtnutí políčka **kompilovat pomocí .NET Nativeho řetězu nástrojů** .   Upozorňujeme však, že Windows Store vždy zkompiluje produkční verzi vaší aplikace s řetězcem nástroje .NET Native.  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a>Zprávy o výjimkách modulu runtime  
 Pro minimalizaci velikosti spustitelného souboru aplikace .NET Native neobsahují úplný text zpráv o výjimkách. V důsledku toho nemusí běhové výjimky vyvolané v sestavení vydaných verzí zobrazovat úplný text zpráv o výjimkách. Místo toho se může text skládat z podřetězce spolu s odkazem na Další informace. Například informace o výjimce mohou vypadat takto:  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Pokud potřebujete zprávu o úplné výjimce, spusťte místo toho sestavení ladění. Například předchozí informace o výjimce z buildu pro vydání se mohou zobrazit v sestavení ladění následujícím způsobem:  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a>Zásobník volání za běhu  
 Z důvodu vkládání a dalších optimalizací může být zásobník volání zobrazený aplikací zkompilováným řetězcem nástroje .NET Native moci jednoznačně identifikovat cestu k výjimce modulu runtime.  
  
 Chcete-li získat úplný zásobník, spusťte místo toho sestavení ladění.  
  
## <a name="see-also"></a>Viz také:

- [Ladění .NET Native univerzálních aplikací pro Windows](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [Začínáme](getting-started-with-net-native.md)
