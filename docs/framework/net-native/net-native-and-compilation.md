---
title: .NET Native a kompilace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e38ae4f3-3e3d-42c3-a4b8-db1aa9d84f85
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5a15ac314590b9b7e240e759b9482eafb7071cd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="net-native-and-compilation"></a>.NET Native a kompilace
Aplikace Windows 8.1 a Windows Desktop aplikace, které cílí na rozhraní.NET Framework jsou napsané v konkrétní programovací jazyk a zkompilovat do převodní jazyk (IL). V době běhu kompilátor za běhu (JIT) zodpovídá za kompilace IL do nativního kódu pro místní počítač, těsně před je metoda spuštěna poprvé. Naproti tomu řetězu .NET Native nástroj převede zdrojového kódu do nativního kódu v době kompilace. Toto téma porovnává .NET Native s jinými technologiemi kompilace k dispozici pro aplikace .NET Framework a také poskytuje praktické přehled o tom, jak .NET Native vytváří nativní kód, který vám může pomoct pochopit, proč výjimky, které se objeví v kódu kompilovat s .NET Nativní se nevyskytují v kompilována kódu.  
  
## <a name="net-native-generating-native-binaries"></a>.NET native: Generování nativní binárních souborů  
 Aplikace, není pomocí .NET Native řetězu nástroj zkompilovaná cílů rozhraní .NET Framework a který se skládá z sestavení aplikace, která zahrnuje následující:  
  
-   [Metadata](../../../docs/standard/metadata-and-self-describing-components.md) sestavení, jeho závislé součásti, obsahuje typy a jejich členy, který popisuje. Metadata slouží pro reflexe a pozdní vazby přístup a v některých případech i nástrojů kompilátoru a sestavení.  
  
-   Implementace kód. Tento postup se skládá operačních kódů převodní jazyk (IL). V době běhu kompilátoru za běhu (JIT) převede jej do nativního kódu pro cílovou platformu.  
  
 Kromě vaší hlavní aplikace sestavení aplikace vyžaduje, aby následující existuje:  
  
-   Žádné další třídy knihovny nebo sestavení třetích stran, které jsou vyžadované vaší aplikace. Tyto sestavení podobně obsahovat metadata, která popisuje sestavení, jeho typy a jejich členy, jakož i IL, který implementuje všechny členy typu.  
  
-   Knihovna tříd rozhraní .NET Framework. Toto je kolekce sestavení, která je nainstalována na místní systém s instalace rozhraní .NET Framework. Sestavení zahrnuty v knihovně tříd rozhraní .NET Framework zahrnovat kompletní sadu metadat a provádění kódu.  
  
-   Modul CLR. Toto je kolekce dynamické knihovny, které provádějí takové služby jako načítání sestavení, správu a uvolňování paměti kolekce paměti, výjimek, kompilace za běhu, vzdálenou komunikaci a zprostředkovatel komunikace s objekty. Jako knihovny tříd je nainstalován modul runtime v místním systému jako součást instalace rozhraní .NET Framework.  
  
 Všimněte si, že celý modul common language runtime, jakož i metadata a IL pro všechny typy v sestavení specifické pro aplikaci, sestavení třetích stran a sestavení systému musí být k dispozici pro aplikaci při spuštění.  
  
## <a name="net-native-and-just-in-time-compilation"></a>Kompilace .NET native a za běhu  
 Vstup pro .NET Native řetězec nástroj je aplikace pro Windows store vytvořené C# nebo Visual Basic – kompilátor. Jinými slovy řetězu .NET Native nástroj zahájí spuštění po dokončení kompilátor jazyka kompilace aplikace pro Windows Store.  
  
> [!TIP]
>  Protože vstup .NET Native IL a metadata zapsána do spravované sestavení, můžete přesto provést generace vlastní kód nebo další vlastní operace pomocí události před sestavením nebo po sestavení nebo změnou soubor projektu nástroje MSBuild.  
>   
>  Kategorie nástroje, které upravit IL a tím zabránit v řetězu .NET nástroj Analýza aplikace IL ale podporované nejsou. Obfuscators jsou nástroje nejdůležitějším tohoto typu.  
  
 V průběhu převodu aplikace na nativní kód IL, řetězu .NET Native nástroj provádí operace, jako je následující:  
  
-   Pro určité cesty kódu, se nahradí kód, který závisí na reflexi a metadat pomocí statické nativního kódu. Například, pokud typ hodnoty nepřepisuje <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> metoda, výchozí testování rovnosti pomocí reflexe načíst <xref:System.Reflection.FieldInfo> objekty, které představují typ hodnoty pole, pak porovná dvě instance hodnoty polí. Při kompilování do nativního kódu, nahradí řetězu .NET Native nástroj reflexe kód a metadata statické porovnání hodnot polí.  
  
-   Pokud je to možné, pokusí se odstranit všechna metadata.  
  
-   Obsahuje v sestaveních konečné aplikaci pouze implementace kód, který je ve skutečnosti vyvolané aplikace. Tímto je ovlivněn zvlášť kód v knihovnách třetích stran a v knihovně tříd rozhraní .NET Framework. V důsledku toho se aplikace už závisí na knihovny třetích stran nebo úplné Framework knihovně tříd rozhraní .NET; Místo toho v jiných výrobců a knihovny tříd rozhraní .NET Framework je kód místní do aplikace.  
  
-   Nahradí úplné CLR refactored modul runtime, který obsahuje především uvolňování paměti. Refactored runtime nachází v knihovně s názvem mrt100_app.dll místní aplikace, který je pouze několik set kilobajtů velikost. To je možné, protože statické propojení eliminuje potřebu mnoho služeb provádí modul common language runtime.  
  
    > [!NOTE]
    >  .NET native používá stejné uvolňování jako standardní common language runtime. V .NET Native uvolňování paměti je ve výchozím nastavení povolená kolekce paměti na pozadí. Další informace o uvolňování paměti najdete v tématu [základy uvolnění paměti](../../../docs/standard/garbage-collection/fundamentals.md).  
  
> [!IMPORTANT]
>  .NET native zkompiluje celý aplikace k nativní aplikaci. Neumožňuje můžete zkompilovat jednoho sestavení obsahující knihovny tříd do nativního kódu tak, aby ji můžete nezávisle volat ze spravovaného kódu.  
  
 Výsledný aplikaci, která je produkovaný řetězu .NET Native nástroj je zapsán do adresář s názvem ilc.out v adresáři ladění nebo verze v adresáři projektu. Obsahuje následující soubory:  
  
-   *\<appName >*.exe, se zakázaným inzerováním spustitelný soubor, který jednoduše převede ovládací prvek speciální `Main` exportovat ve  *\<appName >*.dll.  
  
-   *\<appName >*.dll, Windows dynamické knihovny, který obsahuje všechny kódu aplikace, stejně jako kód z knihovně tříd rozhraní .NET Framework a všechny knihovny třetích stran, které jsou závislé na.  Také obsahuje kód podpory, jako je kód potřebné pro spolupráci s Windows a k serializaci objektů ve vaší aplikaci.  
  
-   mrt100_app.dll, refactored modul runtime, který poskytuje služby modulu runtime, jako je například uvolňování paměti.  
  
 Všechny závislosti jsou zachyceny pomocí APPX manifest aplikace.  Kromě aplikací exe, dll a mrt100_app.dll, které jsou seskupeny přímo v balíček appx to zahrnuje další dva soubory:  
  
-   msvcr140_app.dll, používá mrt100_app.dll knihovny C Runtime (CRT). Je zahrnutý v balíčku odkaz framework.  
  
-   mrt100.dll. Tato knihovna obsahuje funkce, které může zvýšit výkon mrt100_app.dll, i když jeho absenci nezabrání mrt100_app.dll funguje. Je načten z adresáře system32 v místním počítači, pokud je k dispozici.  
  
 Protože řetězu .NET Native nástroj odkazuje implementaci kódu do vaší aplikace jenom v případě, že bude vědět, že aplikace ve skutečnosti vyvolá tento kód a nemusí být součástí aplikace metadata nebo kód implementace vyžaduje v následujících scénářích:  
  
-   Reflexe.  
  
-   Dynamické nebo pozdní vazbou volání.  
  
-   Serializace a deserializace.  
  
-   Zprostředkovatel komunikace s objekty COM.  
  
 Chybí-li nutné metadata nebo implementaci kódu v době běhu .NET Native runtime vyvolá výjimku. Můžete zakázat tyto výjimky a ujistěte se, že řetězu .NET Native nástroj zahrnuje požadovaná metadata a implementaci kódu pomocí [souboru direktivy modulu runtime](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md), soubor XML, který určuje elementy program, jehož metadata nebo implementace kód musí být k dispozici v době běhu a přiřadí zásady modulu runtime k nim. Toto je výchozí soubor direktivy modulu runtime, který je přidán do projektu Windows Store, který se zkompiluje .NET Native řetězcem nástroj:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
  </Application>  
</Directives>  
```  
  
 To umožňuje všechny typy, stejně jako všechny jejich členy, ve všech sestaveních ve vašich balíček aplikace pro reflexe a dynamické volání. Však není povolit, reflexe nebo dynamické aktivace typy v sestavení rozhraní .NET Framework – knihovna tříd. V mnoha případech je to dostačující.  
  
## <a name="net-native-and-ngen"></a>.NET native a NGEN  
 [(Generátor](../../../docs/framework/tools/ngen-exe-native-image-generator.md) (NGEN) kompiluje sestavení do nativního kódu a nainstaluje je do mezipaměti nativních bitových kopií v místním počítači. Nicméně i když NGEN, jako jsou .NET Native vytváří nativního kódu, se liší od .NET Native některé důležité způsoby:  
  
-   Pokud je k dispozici pro konkrétní metody žádné nativních bitových kopií, NGEN spadne zpět na JITing kódu. To znamená, že nativní bitové kopie musí dál zahrnovat metadata a IL v případě, že NGEN musí vrátit zpět k JIT – kompilace. Naproti tomu .NET Native vytváří nativní bitové kopie a nepřecházely k JIT – kompilace. V důsledku toho musí být zachováno pouze metadata jsou požadovaná pro některé úvahy, serializace a spolupráce scénáře.  
  
-   NGEN nadále spoléhají na úplné common language runtime služby, například sestavení načítání, vzdálenou komunikaci, zprostředkovatel komunikace s objekty, správa paměti, uvolňování paměti a v případě potřeby JIT – kompilace. V rozhraní .NET nativní mnoho z těchto služeb jsou buď nepotřebné (JIT – kompilace) nebo jsou přeložit v čase vytvoření buildu a začlenit i metodu v sestavení aplikace. Zbývající služby, které nejdůležitější je uvolňování paměti, jsou součástí mnohem menší, rozdělili runtime s názvem mrt100_app.dll.  
  
-   Obrázky NGEN jsou obvykle křehké. Například opravy nebo změně závislost obvykle vyžaduje, aby sestavení, které ho používají také NGENed znovu. To platí hlavně systému sestavení v knihovně tříd rozhraní .NET Framework. .NET Native naopak umožňuje aplikacím zpracovat nezávisle na sobě.  
  
## <a name="see-also"></a>Viz také  
 [Metadata a komponenty popisující samy sebe](../../../docs/standard/metadata-and-self-describing-components.md)  
 [Uvnitř .NET Native (Video na kanálu 9)](http://channel9.msdn.com/Shows/Going+Deep/Inside-NET-Native)  
 [Reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
 [Řešení potíží s .NET native obecné](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
