---
title: .NET Native a kompilace
ms.date: 03/30/2017
ms.assetid: e38ae4f3-3e3d-42c3-a4b8-db1aa9d84f85
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a15d30ea4d6e0f4456460248e96428419117d85
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049443"
---
# <a name="net-native-and-compilation"></a>.NET Native a kompilace

Windows 8.1 aplikací a desktopových aplikací pro Windows, které cílí na the.NET Framework, se zapisují do konkrétního programovacího jazyka a zkompiluje se do jazyka IL (Intermediate Language). Za běhu zodpovídá kompilátor JIT (just-in-time) za kompilace IL do nativního kódu pro místní počítač těsně před prvním provedením metody. Naproti tomu řetěz nástrojů .NET Native převádí zdrojový kód do nativního kódu v době kompilace. Toto téma porovnává .NET Native s dalšími technologiemi kompilace dostupnými pro .NET Framework aplikace a také poskytuje praktický přehled o tom, jak .NET Native vytváří nativní kód, který vám pomůže pochopit, proč výjimky, ke kterým dochází v kódu zkompilovaném pomocí .NET. Nativní neproběhne v kódu kompilovaném JIT.

## <a name="net-native-generating-native-binaries"></a>.NET Native: Generování nativních binárních souborů

Aplikace, která cílí na .NET Framework a která není zkompilována pomocí .NET Nativeho řetězu nástroje, se skládá ze sestavení vaší aplikace, které zahrnuje následující:

- [Metadata](../../standard/metadata-and-self-describing-components.md) , která popisují sestavení, jeho závislosti, typy, které obsahuje, a jejich členy. Metadata se používají pro reflexi a přístup s pozdní vazbou a v některých případech také pomocí kompilátoru a nástrojů sestavení.

- Implementační kód. Skládá se z operačních kódů jazyka IL (Intermediate Language). Za běhu je kompilátor JIT (just-in-time) překládá do nativního kódu pro cílovou platformu.

 Kromě vašeho hlavního sestavení aplikace aplikace vyžaduje, aby byla k dispozici následující:

- Všechny další knihovny tříd nebo sestavení třetích stran, které vaše aplikace vyžaduje. Tato sestavení podobně zahrnují metadata, která popisují sestavení, jeho typy a jejich členy, a také IL, který implementuje všechny členy typu.

- Knihovna tříd .NET Framework. Toto je kolekce sestavení, která jsou nainstalována v místním systému s instalací .NET Framework. Sestavení zahrnutá do knihovny tříd .NET Framework zahrnují úplnou sadu metadat a implementačního kódu.

- Modul CLR (Common Language Runtime) Jedná se o kolekci knihoven DLL, které provádějí takové služby jako načítání sestavení, správu paměti a uvolňování paměti, zpracování výjimek, kompilaci za běhu, vzdálené komunikace a interoperabilitu. Podobně jako u knihovny tříd je modul runtime nainstalován v místním systému jako součást instalace .NET Framework.

Všimněte si, že celý modul CLR (Common Language Runtime) i metadata a IL pro všechny typy v sestaveních specifických pro aplikace, sestavení třetích stran a systémová sestavení musí být k dispozici, aby bylo možné aplikaci úspěšně spustit.

## <a name="net-native-and-just-in-time-compilation"></a>.NET Native a kompilace za běhu

Vstup pro .NET Native řetězec nástroje je aplikace pro Windows Store vytvořená kompilátorem C# nebo Visual Basic. Jinými slovy řetěz nástrojů .NET Native začíná prováděním, když kompilátor jazyka dokončil kompilaci aplikace pro Windows Store.

> [!TIP]
> Vzhledem k tomu, že vstup pro .NET Native je IL a metadata zapsaná do spravovaných sestavení, můžete i nadále provádět vlastní generování kódu nebo jiné vlastní operace pomocí událostí před sestavením nebo po sestavení nebo úpravou souboru projektu MSBuild.
>
> Nicméně kategorie nástrojů, které upravují IL a zabraňují tak řetězci nástrojů .NET z analýzy IL aplikace, nejsou podporovány. Pro tento typ jsou nejvýznamnější nástroje.

V průběhu převodu aplikace z IL na nativní kód řetěz nástroje .NET Native provádí operace podobné následujícímu:

- Pro určité cesty kódu nahrazuje kód, který spoléhá na reflexi a metadata se statickým nativním kódem. Například pokud typ hodnoty nepřepisuje <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> metodu, výchozí test rovnosti používá reflexi k načtení <xref:System.Reflection.FieldInfo> objektů, které reprezentují pole hodnotového typu, a pak porovná hodnoty pole dvou instancí. Při kompilování do nativního kódu řetězec nástroje .NET Native nahradí kód reflexe a metadata statickým porovnáním hodnot polí.

- Pokud je to možné, pokusí se eliminovat všechna metadata.

- Obsahuje v konečných sestaveních aplikace pouze kód implementace, který je skutečně vyvolán aplikací. To se týká zejména kódu v knihovnách třetích stran a v knihovně tříd .NET Framework. V důsledku toho aplikace již nezávisí na knihovně třetích stran nebo na úplné .NET Framework knihovně tříd. místo toho je kód v knihovnách tříd třetích stran a .NET Framework pro aplikaci nyní místní.

- Nahrazuje úplný CLR pomocí refaktoringu modulu runtime, který primárně obsahuje systém uvolňování paměti. Refaktored runtime se nachází v knihovně s názvem mrt100_app. dll, která je pro aplikaci místní a má velikost jenom několik set kilobajtů. To je možné, protože statické propojení eliminuje potřebu mnoha služeb, které provádí modul CLR (Common Language Runtime).

  > [!NOTE]
  > .NET Native používá stejný systém uvolňování paměti jako standardní modul CLR (Common Language Runtime). V .NET Native uvolňování paměti na pozadí je ve výchozím nastavení povolené uvolňování paměti na pozadí. Další informace o uvolňování paměti najdete v tématu [Základy uvolňování paměti](../../standard/garbage-collection/fundamentals.md).

> [!IMPORTANT]
> .NET Native zkompiluje celou aplikaci do nativní aplikace. Neumožňuje kompilovat jedno sestavení, které obsahuje knihovnu tříd do nativního kódu, aby jej bylo možné volat nezávisle ze spravovaného kódu.

Výsledná aplikace, která je vytvořena řetězcem nástroje .NET Native, je zapsána do adresáře s názvem ilc. out v adresáři pro ladění nebo vydání adresáře projektu. Skládá se z následujících souborů:

- AppName >. exe, spustitelný soubor se zástupnými procedurami, který `Main` jednoduše přenáší řízení na speciální export v  *\<AppName >* . dll.  *\<*

- AppName >. dll, knihovna dynamického propojení Windows, která obsahuje veškerý kód vaší aplikace, a kód z knihovny tříd .NET Framework a všechny knihovny třetích stran, na kterých máte závislost.  *\<*  Obsahuje také kód podpory, jako je třeba kód potřebný pro vzájemnou spolupráci s Windows a serializaci objektů ve vaší aplikaci.

- mrt100_app. dll, refaktored runtime, který poskytuje běhové služby, jako je uvolňování paměti.

 Všechny závislosti jsou zachyceny manifestem APPX aplikace.  Kromě exe aplikace, knihovny DLL a mrt100_app. dll, které jsou přímo v balíčku appx, to zahrnuje dva další soubory:

- msvcr140_app. dll, Knihovna CRT (C run-time), kterou používá mrt100_app. dll. Obsahuje odkaz na rozhraní v balíčku.

- mrt100.dll. Tato knihovna obsahuje funkce, které mohou zlepšit výkon souboru mrt100_app. dll, i když jeho absence nebrání v fungování mrt100_app. dll. Je načten z adresáře System32 na místním počítači, pokud je k dispozici.

Vzhledem k tomu, že řetězec nástroje .NET Native propojuje implementační kód do vaší aplikace pouze v případě, že ví, že vaše aplikace skutečně vyvolá tento kód, nemusí být do vaší aplikace zahrnuty metadata nebo implementační kód vyžadovaný v následujících scénářích:

- Operace.

- Dynamické nebo pozdní vyvolání vazby.

- Serializace a deserializace.

- Zprostředkovatel komunikace s objekty COM.

Pokud v době běhu chybí potřebná metadata nebo implementační kód, modul runtime .NET Native vyvolá výjimku. Můžete zabránit těmto výjimkám a zajistit, aby řetěz nástrojů .NET Native zahrnoval požadovaná metadata a implementační kód, pomocí [souboru XML direktiv](runtime-directives-rd-xml-configuration-file-reference.md), soubor XML, který určí prvky programu, jejichž metadata nebo implementace kód musí být k dispozici za běhu a přiřadí jim běhové zásady. Následuje výchozí soubor direktiv modulu runtime, který je přidán do projektu Windows Store, který je zkompilován pomocí .NET Nativeho řetězu nástrojů:

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
  </Application>
</Directives>
```

To umožňuje všem typům a všem jejich členům ve všech sestaveních v balíčku aplikace pro reflexi a dynamické vyvolání. Nicméně nepovoluje reflexi nebo dynamickou aktivaci typů v sestaveních knihovny tříd .NET Framework. V mnoha případech to postačuje.

## <a name="net-native-and-ngen"></a>.NET Native a NGEN

[(Generátor nativních bitových kopií](../tools/ngen-exe-native-image-generator.md) (NGen) zkompiluje sestavení do nativního kódu a nainstaluje je do mezipaměti nativních imagí v místním počítači. Nicméně i když NGEN, jako je například .NET Native, vytváří nativní kód, liší se od .NET Native nějakými značnými způsoby:

- Pokud není pro konkrétní metodu k dispozici žádná nativní image, NGEN se vrátí k JITing kódu. To znamená, že nativní bitové kopie musí nadále zahrnovat metadata a IL v případě, že NGEN musí přejít zpět na kompilaci JIT. Naproti tomu .NET Native vytvoří pouze nativní bitové kopie a nevrátí se do kompilace JIT. V důsledku toho musí být zachována pouze metadata požadovaná pro scénáře pro odraz, serializaci a spolupráci.

- Služba NGEN nadále spoléhá na úplný modul CLR (Common Language Runtime) pro služby, jako je načítání sestavení, Vzdálená komunikace, spolupráce, Správa paměti, uvolňování paměti a v případě potřeby i kompilace JIT. V .NET Native mnohé z těchto služeb jsou buď zbytečné (kompilace JIT), nebo jsou vyřešeny v době sestavení a zahrnuty v sestavení aplikace. Zbývající služby, jejichž nejdůležitější z nich je uvolňování paměti, jsou součástí mnohem menšího, refaktoringového modulu runtime s názvem mrt100_app. dll.

- Image NGEN mají v úmyslu být křehké. Například oprava nebo změna závislosti obvykle vyžaduje, aby byla sestavení, která používají, také znovu NGENed. To platí zejména pro systémová sestavení v knihovně tříd .NET Framework. Naproti tomu .NET Native umožňuje aplikacím, aby byly obsluhovány nezávisle na sobě.

## <a name="see-also"></a>Viz také:

- [Metadata a komponenty popisující samy sebe](../../standard/metadata-and-self-describing-components.md)
- [Uvnitř .NET Native (video kanálu 9)](https://channel9.msdn.com/Shows/Going+Deep/Inside-NET-Native)
- [Reflexe a .NET Native](reflection-and-net-native.md)
- [Obecné řešení potíží s .NET Native](net-native-general-troubleshooting.md)
