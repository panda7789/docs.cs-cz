---
title: Výjimky za běhu v nativních aplikací .NET
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 12df2ef7bf6e86a60dfa4c130f35969e72ac5211
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180940"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>Výjimky za běhu v nativních aplikací .NET
Je důležité otestovat sestavení verze aplikace univerzální platformy Windows na cílových platformách, protože konfigurace ladění a vydání jsou zcela odlišné. Ve výchozím nastavení používá konfigurace ladění ke kompilaci aplikace runtime .NET Core, ale konfigurace vydání používá .NET Native ke kompilaci aplikace do nativního kódu.  
  
> [!IMPORTANT]
> Informace o práci s [ChybějícíMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) výjimky, které se mohou vyskytnou při testování vydání verze aplikace, naleznete v části Krok 4: Ručně vyřešit chybějící metadata: v [tématu Začínáme,](getting-started-with-net-native.md) jakož i [Reflexe a .NET nativní](reflection-and-net-native.md) a [runtime směrnice (rd.xml) Konfigurační soubor Odkaz](runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Ladění a vydání sestavení  
 Při ladění sestavení provede proti .NET Core runtime, nebyl akompilován do nativního kódu. Díky tomu jsou všechny služby běžně poskytované za běhu k dispozici pro vaši aplikaci.  
  
 Na druhou stranu se sestavení verze zkompiluje do nativního kódu pro své cílové platformy, odebere většinu závislostí na externích runčasech a knihovnách a silně optimalizuje kód pro maximální výkon.  
  
 Při ladění vydání sestavení, které jsou kompilovány pomocí .NET Native:  
  
- Použijete ladicí modul .NET Native, který se liší od běžných ladicích nástrojů .NET.  
  
- Velikost spustitelného souboru je co nejvíce snížena. Jedním ze způsobů, které .NET Native zmenšuje velikost spustitelného souboru, je výrazné oříznutí zpráv výjimek modulu runtime, což je téma popsané podrobněji v části [Zprávy výjimek modulu Runtime.](#Messages)  
  
- Váš kód je silně optimalizován. To znamená, že vkládání se používá, kdykoli je to možné. (Vkládání přesune kód z externích rutin do volající rutiny.)   Skutečnost, že .NET Native poskytuje specializované runtime a implementuje agresivní vkládání ovlivňuje zásobník volání, který se zobrazí při ladění.  Další informace naleznete v části [Zásobník volání runtime.](#CallStack)  
  
> [!NOTE]
> Můžete určit, zda ladění a vydání sestavení jsou kompilovány s řetězcem nástrojů .NET Nativní kontrolou nebo zrušením zaškrtnutí **compile with .NET Nativní řetězec nástrojů** box.   Upozorňujeme však, že Windows Store bude vždy zkompilovat produkční verzi vaší aplikace pomocí řetězce nástrojů .NET Native.  
  
<a name="Messages"></a>
## <a name="runtime-exception-messages"></a>Zprávy o výjimce za běhu  
 Chcete-li minimalizovat velikost spustitelného souboru aplikace, nativní rozhraní .NET neobsahuje úplný text zpráv výjimek. V důsledku toho runtime výjimky vyvolány v sestavení verze nemusí zobrazit úplný text zprávy výjimky. Místo toho text může sestávat z podřetězce spolu s odkazem následovat další informace. Informace o výjimce se mohou například zobrazit jako:  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Pokud potřebujete úplnou zprávu o výjimce, spusťte místo toho sestavení ladění. Například předchozí informace o výjimce z verze sestavení se může zobrazit takto v sestavení ladění:  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>
## <a name="runtime-call-stack"></a>Zásobník volání za běhu  
 Z důvodu vkládání a další optimalizace zásobníku volání zobrazené aplikací zkompilované řetězce nástrojů .NET Nativní nemusí pomoci jasně identifikovat cestu k výjimce za běhu.  
  
 Chcete-li získat celý zásobník, spusťte sestavení ladění místo.  
  
## <a name="see-also"></a>Viz také

- [Ladění nativních univerzálních aplikací systému Windows .NET](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [Začínáme](getting-started-with-net-native.md)
