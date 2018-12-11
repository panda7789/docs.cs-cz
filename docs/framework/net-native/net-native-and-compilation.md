---
title: .NET Native a kompilace
ms.date: 03/30/2017
ms.assetid: e38ae4f3-3e3d-42c3-a4b8-db1aa9d84f85
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a89474ddfe3bcde1c44271818b7e3c730469f48
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152523"
---
# <a name="net-native-and-compilation"></a>.NET Native a kompilace
Aplikace Windows 8.1 a Windows desktopových aplikací, které jsou cíleny na rozhraní.NET Framework jsou napsané v konkrétním programovacím jazykem a zkompilovány do (IL intermediate language). Za běhu kompilátor just-in-time (JIT) zodpovídá za kompilace IL do nativního kódu pro místní počítač, těsně před prvním je metoda spuštěna. Naproti tomu .NET Native řetězce nástrojů převede zdrojový kód do nativního kódu v době kompilace. Toto téma porovnává .NET Native s jinými technologiemi kompilace k dispozici pro aplikace rozhraní .NET Framework a také poskytuje praktické přehled jak .NET Native vytváří nativní kód, který vám pomůžou pochopit, proč výjimky, ke kterým dochází v kód zkompilovaný s .NET Nativní nedojde v kód zkompilovaný kompilátorem JIT.  
  
## <a name="net-native-generating-native-binaries"></a>.NET native: Generuje se nativní binární soubory  
 Aplikace, že zaměřené na rozhraní .NET Framework a není zkompilován s použitím .NET Native řetězce nástrojů se skládá z sestavení aplikace, která zahrnuje následující:  
  
-   [Metadata](../../../docs/standard/metadata-and-self-describing-components.md) , který popisuje sestavení, jeho závislostí, obsahuje typy a jejich členy. Metadata používá reflexi a přístup s pozdní vazbou a v některých případech kompilátor a nástroje sestavení také.  
  
-   Implementační kód. To se skládá z operační kódy (IL intermediate language). Za běhu kompilátor just-in-time (JIT) přeloží ho do nativního kódu pro cílovou platformu.  
  
 Kromě sestavení hlavní aplikace aplikace vyžaduje, aby následující k dispozici:  
  
-   Další knihovny tříd nebo sestavení třetích stran, které jsou vyžadované vaší aplikace. Mezi tato sestavení podobně patří metadata, která popisují sestavení, jeho typy a jejich členy, jakož i IL, který implementuje všechny členy typu.  
  
-   Knihovna tříd rozhraní .NET Framework. To je soubor sestavení, který je nainstalován v místním systému s instalací rozhraní .NET Framework. Sestavení součástí knihovny tříd rozhraní .NET Framework obsahují kompletní sadu metadat a implementace kódu.  
  
-   Modul common language runtime. Toto je kolekce dynamické knihovny, které provádějí tyto služby jako načítání sestavení, správy a uvolňování paměti kolekce paměti, zpracování výjimek, kompilace just-in-time, vzdálené komunikace a spolupráce. Stejně jako knihovna tříd je nainstalován modul runtime v místním systému jako součást instalace rozhraní .NET Framework.  
  
 Všimněte si, že celý modul common language runtime, jakož i metadata a IL pro všechny typy v sestavení specifická pro aplikaci, sestavení třetích stran a systémová sestavení musí být k dispozici pro aplikaci úspěšně vykonat.  
  
## <a name="net-native-and-just-in-time-compilation"></a>Kompilace .NET native a just-in-time  
 Vstup pro .NET Native řetězce nástrojů je aplikace sestavena ze storu Windows C# nebo kompilátor jazyka Visual Basic. Jinými slovy .NET Native řetězce nástrojů začíná spuštění, když kompilátor jazyka dokončil kompilace aplikace pro Windows Store.  
  
> [!TIP]
>  Vzhledem k tomu, že jazyk IL a metadata zapsaná do spravovaných sestavení vstup do .NET Native se můžete stále provádět vytváření vlastního kódu nebo jiných vlastních operací pomocí události před sestavením nebo po sestavení nebo úpravou souboru projektu MSBuild.  
>   
>  Kategorií nástrojů, které upravují IL a tím zabránit řetězce nástrojů .NET v analýze vaší aplikace IL ale podporované nejsou. Obfuscators jsou nejdůležitější nástroje tohoto typu.  
  
 .NET Native řetězce nástrojů tím, že převádíte aplikace z IL na nativní kód, provádí operace, jako je následující:  
  
-   Pro některé cesty kódu, nahradí kód, který závisí na reflexi a metadat pomocí statické nativního kódu. Například, pokud nepřepisuje typ hodnoty <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> metody výchozí testování rovnosti používá reflexi k načtení <xref:System.Reflection.FieldInfo> objekty, které představují typ hodnoty polí, potom porovnává hodnoty polí dvě instance. Při kompilaci do nativního kódu, nahradí .NET Native řetězce nástrojů reflexe kódu a metadata statické porovnání hodnot polí.  
  
-   Kde je to možné, pokusí se odstranit všechna metadata.  
  
-   Zahrnuje poslední aplikace sestavení pouze implementační kód, který je ve skutečnosti vyvolala aplikace. Tímto je ovlivněn zejména kód v knihovnách třetích stran a v knihovně tříd rozhraní .NET Framework. V důsledku toho již aplikace závisí na knihovny třetích stran nebo úplné knihovny tříd .NET Framework; Kód třetích stran a knihovny tříd rozhraní .NET Framework je místo toho teď vůči aplikaci lokální.  
  
-   Nahradí úplné CLR refaktorovaný modulu runtime, která primárně obsahuje systému uvolňování paměti. Refaktorovaný modulu runtime se nachází v knihovně s názvem mrt100_app.dll, který je vůči aplikaci lokální a je jen několik stovek kilobajtů velikost. To je možné, protože statické propojování odstraňuje potřebu řady služeb, prováděné modul common language runtime.  
  
    > [!NOTE]
    >  .NET native používá stejné systému uvolňování paměti jako standard common language runtime. V .NET Native systému uvolňování paměti uvolňování paměti na pozadí ve výchozím nastavení zapnutá. Další informace o uvolňování paměti naleznete v tématu [základy kolekce paměti](../../../docs/standard/garbage-collection/fundamentals.md).  
  
> [!IMPORTANT]
>  .NET native zkompiluje celé aplikace do nativní aplikace. Neumožňuje je pro kompilaci jednoho sestavení, který obsahuje knihovnu tříd do nativního kódu, takže může být volána nezávisle na sobě ze spravovaného kódu.  
  
 Výsledná aplikace, který je vytvořen .NET Native řetězce nástrojů se zapíše do adresáře s názvem ilc.out v adresáři ladění nebo vydání v adresáři projektu. Skládá se z následujících souborů:  
  
-   *\<název_aplikace >*.exe, zástupná procedura spustitelný soubor, který jednoduše převede ovládací prvek speciální `Main` export v  *\<název_aplikace >*.dll.  
  
-   *\<název_aplikace >*.dll, dynamickou Windows propojit knihovnu, která obsahuje váš kód aplikace, stejně jako kód z knihovny tříd rozhraní .NET Framework a všechny knihovny třetích stran, které jsou závislé na.  Také obsahuje kód podpory, jako je kód pro spolupráci s Windows a k serializaci objektů ve vaší aplikaci.  
  
-   mrt100_app.dll, refaktorovaný modulu runtime, který poskytuje služby modulu runtime, jako je například uvolňování paměti.  
  
 Všechny závislosti jsou zachyceny manifestu APPX aplikace.  Kromě aplikace exe, dll a mrt100_app.dll, které jsou spojeny přímo v balíčku appx to obsahuje dva další soubory:  
  
-   msvcr140_app.dll, knihovny C run-time (CRT), používané mrt100_app.dll. Je součástí odkaz na rozhraní v balíčku.  
  
-   mrt100.dll. Tuto knihovnu zahrnuje funkce, které může zlepšit výkon mrt100_app.dll, i když neexistuje nebrání mrt100_app.dll fungovat. Načte se v adresáři system32 na místním počítači, pokud je k dispozici.  
  
 .NET Native řetězce nástrojů odkazy implementační kód do vaší aplikace pouze v případě, že ví, že vaše aplikace ve skutečnosti vyvolá tento kód, takže metadata nebo implementační kód vyžaduje v následujících scénářích nemusí být součástí vaší aplikace:  
  
-   Reflexe.  
  
-   Volání dynamického nebo s pozdní vazbou.  
  
-   Serializace a deserializace.  
  
-   Komunikace s objekty COM  
  
 Pokud chybí nezbytné metadata nebo provádění kódu za běhu, modul runtime .NET Native, dojde k výjimce. Můžete zakázat tyto výjimky a ujistěte se, .NET Native řetězce nástrojů obsahuje požadované metadat a implementace kódu s použitím [soubor direktiv modulu runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md), soubor XML, který určuje prvky programu, jejichž metadat nebo implementační kód musí být k dispozici za běhu a přiřadí zásady modulu runtime k nim. Toto je výchozí soubor direktivy modulu runtime, který je přidán do projektu Windows Store, který je zkompilován s .NET Native řetězce nástrojů:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
  </Application>  
</Directives>  
```  
  
 Díky tomu všech typů, stejně jako všechny jejich členy, všechna sestavení v balíčku aplikace pro reflexi a dynamické vyvolání. Však neumožňuje reflexe nebo dynamické aktivace typů v sestavení knihovny tříd .NET Framework. V mnoha případech jde dostatečné.  
  
## <a name="net-native-and-ngen"></a>.NET native a technologie NGEN  
 [(Native Image Generator](../../../docs/framework/tools/ngen-exe-native-image-generator.md) (NGEN) kompiluje sestavení do nativního kódu a nainstaluje je do mezipaměti nativních bitových kopií v místním počítači. Nicméně i když NGEN, jako je .NET Native, vytvoří nativní kód, se liší od .NET Native v některých ohledech významné:  
  
-   Pokud žádné nativní bitové kopie je k dispozici pro konkrétní metody, NGEN spadne zpět na JITing kódu. To znamená, že nativní bitové kopie musí i nadále zahrnují metadata a IL v případě, že je potřeba vrátit zpět k JIT kompilaci NGEN. Naproti tomu .NET Native vytváří nativní bitové kopie a nepřecházel k JIT kompilaci. V důsledku toho musí být zachovány jenom metadata jsou požadovaná pro některé úvahy, serializace a spolupráce scénáře.  
  
-   NGEN nadále Spolehněte se na úplné common language runtime pro služby, jako je vzdálené komunikace, spolupráce, správa paměti, uvolňování paměti, načítání sestavení a v případě potřeby, kompilace JIT. V rozhraní .NET Native mnoho z těchto služeb jsou buď zbytečné (kompilace JIT) nebo jsou vyřešené v okamžiku sestavení a zapojit do sestavení aplikace. Zbývající služeb, z nichž nejdůležitější je uvolňování paměti, jsou zahrnuté v mnohem menší, refaktorovaný modulu runtime s názvem mrt100_app.dll.  
  
-   Obrázků NGEN bývají křehké. Třeba opravu nebo změňte na závislost obvykle vyžaduje, aby sestavení, které ho používají také re NGENed. To platí hlavně systémová sestavení v knihovně tříd rozhraní .NET Framework. .NET Native naproti tomu umožňuje aplikacím, ke zpracování nezávisle na mezi sebou.  
  
## <a name="see-also"></a>Viz také  
 [Metadata a komponenty popisující samy sebe](../../../docs/standard/metadata-and-self-describing-components.md)  
 [Uvnitř .NET Native (Video pro kanál 9)](https://channel9.msdn.com/Shows/Going+Deep/Inside-NET-Native)  
 [Reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
 [Obecné řešení potíží s .NET Native](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
