---
title: Sestavení v .NET
ms.date: 08/15/2019
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.openlocfilehash: f85fef37ac952c91ac73570f26d80d8a46f4eedf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156502"
---
# <a name="assemblies-in-net"></a>Sestavení v .NET

Sestavení tvoří základní jednotky nasazení, správy verzí, opakovaného použití, oboru aktivace a oprávnění zabezpečení pro . NET-založené aplikace. Sestavení je kolekce typů a prostředků, které jsou vytvořeny tak, aby vzájemně spolupracovaly a tvořily logickou jednotku funkčnosti. Sestavení mají podobu spustitelných souborů (*EXE*) nebo dynamické knihovny odkazů (*DLL*) a jsou stavebními kameny aplikací .NET. Poskytují běžný jazyk runtime s informacemi, které potřebuje znát implementace typu.

V rozhraní .NET Core a rozhraní .NET Framework můžete sestavit sestavení z jednoho nebo více souborů zdrojového kódu. V rozhraní .NET Framework mohou sestavení obsahovat jeden nebo více modulů. To umožňuje naplánované větší projekty tak, aby několik vývojářů mohlo pracovat na samostatných zdrojových kódových souborech nebo modulech, které jsou kombinovány za účelem vytvoření jednoho sestavení. Další informace o modulech naleznete v [tématu How to: Build a multifile assembly](../../framework/app-domains/build-multifile-assembly.md).

Sestavení mají následující vlastnosti:

- Sestavení jsou implementována jako soubory *EXE* nebo *DLL.*

- U knihoven, které cílí na rozhraní .NET Framework, můžete sdílet sestavení mezi aplikacemi jejich vložením do [globální mezipaměti sestavení (GAC).](../../framework/app-domains/gac.md) Před zahrnutím do gac je nutné sestavení silného názvu. Další informace naleznete [v tématu Sestavení s názvem Strong](strong-named.md).

- Sestavení jsou načtena do paměti pouze v případě, že jsou požadována. Pokud nejsou použity, nejsou načteny. To znamená, že sestavení může být efektivní způsob, jak spravovat prostředky ve větších projektech.

- Můžete programově získat informace o sestavení pomocí reflexe. Další informace naleznete v [tématu Reflexe (C#)](../../csharp/programming-guide/concepts/reflection.md) nebo [Reflexe (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Sestavení můžete načíst pouze ke kontrole <xref:System.Reflection.MetadataLoadContext> pomocí třídy v <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> .NET Core a metody or v rozhraní .NET Core a .NET Framework.

## <a name="assemblies-in-the-common-language-runtime"></a>Sestavení v zaběhu společného jazyka

Sestavení poskytují běžný jazyk runtime s informacemi, které potřebuje znát implementace typu. V modulu runtime neexistuje typ mimo kontext sestavení.

Sestavení definuje následující informace:

- Kód, který spustí běžný jazyk runtime. Všimněte si, že každé sestavení `DllMain` `WinMain`může `Main`mít pouze jeden vstupní bod: , , nebo .

- Hranice zabezpečení. Sestavení je jednotka, ve které jsou požadována a udělována oprávnění. Další informace o hranicích zabezpečení v sestaveních naleznete v [tématu Aspekty zabezpečení sestavení](security-considerations.md).

- Hranice typu. Jednotlivé identity typu zahrnují název sestavení, ve kterém se nachází. Typ s názvem `MyType`, který je načten v oboru jednoho sestavení, není stejný jako typ s názvem `MyType`, který je načten v oboru jiného sestavení.

- Hranice referenčního oboru. [Manifest sestavení](#assembly-manifest) obsahuje metadata, která se používají pro řešení typů a splnění požadavků na prostředky. Manifest určuje typy a prostředky vystavit mimo sestavení a vyjmenovává další sestavení, na kterých závisí. Kód zprostředkujícího jazyka (MSIL) společnosti Microsoft v přenosném spustitelném souboru (PE) nebude spuštěn, pokud nebude mít přidružený [manifest sestavení](#assembly-manifest).

- Hranice verze. Sestavení je nejmenší verzí jednotky v běžném jazyce runtime. Všechny typy a prostředky ve stejném sestavení jsou verzí jako jednotka. [Manifest sestavení](#assembly-manifest) popisuje závislosti verze, které zadáte pro všechna závislá sestavení. Další informace o správu verzí naleznete v [tématu Správa verzí sestavení](versioning.md).

- Jednotka pro nasazení. Při spuštění aplikace je nutné, aby byla k dispozici pouze ta sestavení, která aplikace zpočátku volá. Ostatní sestavení, jako jsou například sestavení obsahující prostředky lokalizace nebo třídy nástrojů, lze načíst na vyžádání. To umožňuje, aby aplikace byly jednoduché a tenké při prvním stažení. Další informace o nasazení sestavení naleznete v tématu [Nasazení aplikací](../../framework/deployment/index.md).

- Souběžně s popravčí jednotkou. Další informace o spuštění více verzí sestavení naleznete v tématu [sestavení a souběžné spuštění](side-by-side-execution.md).

## <a name="create-an-assembly"></a>Vytvoření sestavy

Sestavení mohou být statická nebo dynamická. Statická sestavení jsou uložena na disku v přenosných spustitelných souborech (PE). Statická sestavení mohou zahrnovat rozhraní, třídy a prostředky, jako jsou rastrové obrázky, soubory JPEG a další soubory prostředků. Můžete také vytvořit dynamická sestavení, která jsou spuštěna přímo z paměti a nejsou uložena na disk před spuštěním. Na disk můžete dynamická sestavení uložit až poté, co jsou spuštěna.

Existuje několik způsobů vytváření sestavení. Můžete použít vývojové nástroje, jako je například Visual Studio, které můžete vytvářet soubory *DLL* nebo *EXE.* Pomocí nástrojů sady Windows SDK můžete vytvářet sestavení s moduly z jiných vývojových prostředí. K vytvoření dynamických sestavení můžete také <xref:System.Reflection.Emit?displayProperty=nameWithType>použít rozhraní API pro běžné běhové běhy jazyka, například .

Kompilujte sestavení jejich sestavením v sadě Visual Studio, jejich vytvářením pomocí nástrojů rozhraní příkazového řádku .NET Core nebo sestavením rozhraní .NET Framework pomocí kompilátoru příkazového řádku. Další informace o sestavenísestavení pomocí rozhraní CLI jádra .NET naleznete [v tématu přehled rozhraní .NET Core CLI](../../core/tools/index.md). Vytváření sestavení s kompilátory příkazového řádku naleznete v [tématu sestavení příkazového řádku s csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) pro C#nebo [Sestavení z příkazového řádku](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) pro jazyk Visual Basic.

> [!NOTE]
> Chcete-li vytvořit sestavení v sadě Visual Studio, v nabídce **Sestavení** vyberte **Build**.

## <a name="assembly-manifest"></a>Manifest sestavení

Každé sestavení má soubor *manifestu sestavení.* Podobně jako obsah obsahuje manifest sestavení:

- Identita sestavení (jeho název a verze).

- Tabulka souborů popisující všechny ostatní soubory, které tvoří sestavení, například jiná sestavení, která jste vytvořili a na která se soubor *EXE* nebo *DLL* spoléhá, na bitmapové soubory nebo soubory Readme.

- *Seznam odkazů sestavení*, který je seznamem všech externích závislostí, například *DLL*s nebo jiných souborů. Odkazy na sestavení obsahují odkazy na globální i soukromé objekty. Globální objekty jsou k dispozici pro všechny ostatní aplikace. V .NET Core globální objekty jsou spojeny s konkrétní .NET Core runtime. V rozhraní .NET Framework jsou globální objekty umístěny v globální mezipaměti sestavení (GAC). *System.IO.dll* je příkladem sestavení v GAC. Soukromé objekty musí být na úrovni adresáře v adresáři, ve kterém je aplikace nainstalovaná, nebo pod ním.

Vzhledem k tomu, že sestavení obsahují informace o obsahu, správu verzí a závislostech, aplikace, které je používají, nemusí spoléhat na externí zdroje, jako je například registr v systémech Windows, aby fungovaly správně. Sestavení snižují konflikty *dll* a usnadňují jejich spolehlivost a snadnější nasazení aplikací. V mnoha případech můžete nainstalovat . NET jednoduše zkopírováním svých souborů do cílového počítače. Další informace naleznete v [tématu Manifest sestavení](manifest.md).

## <a name="add-a-reference-to-an-assembly"></a>Přidání odkazu na sestavení

Chcete-li použít sestavení v aplikaci, musíte na něj přidat odkaz. Jakmile je odkazováno na sestavení, všechny přístupné typy, vlastnosti, metody a další členy jeho oborů názvů jsou k dispozici pro vaši aplikaci, jako kdyby jejich kód byl součástí zdrojového souboru.

> [!NOTE]
> Většina sestavení z knihovny tříd .NET je odkazována automaticky. Pokud sestavení systému není automaticky odkazováno, pro .NET Core, můžete přidat odkaz na balíček NuGet, který obsahuje sestavení. Buď použijte Správce balíčků NuGet v sadě Visual Studio, nebo přidejte element [ \<PackageReference>](../../core/tools/dependencies.md#the-packagereference-element) pro sestavení do projektu *.csproj* nebo *.vbproj.* V rozhraní .NET Framework můžete přidat odkaz na sestavení pomocí dialogového okna Přidat `-reference` **odkaz** v sadě Visual Studio nebo pomocí možnosti příkazového řádku pro kompilátory jazyka [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) nebo [Visual Basic.](../../visual-basic/reference/command-line-compiler/reference.md)

V c#, můžete použít dvě verze stejného sestavení v jedné aplikaci. Další informace naleznete v tématu [extern alias](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="related-content"></a>Související obsah

|Nadpis|Popis|
|-----------|-----------------|
|[Obsah sestavení](contents.md)|Prvky, které tvoří sestavení.|
|[Manifest sestavení](manifest.md)|Data v manifestu sestavení a způsob, jakým je uložen v sestaveních.|
|[Globální mezipaměť sestavení](../../framework/app-domains/gac.md)|Jak GAC ukládá a používá sestavení.|
|[Sestavení se silným názvem](strong-named.md)|Charakteristiky sestavení se silným názvem.|
|[Důležité informace o zabezpečení sestavení](security-considerations.md)|Jak zabezpečení funguje s sestaveními.|
|[Správa verzí sestavení](versioning.md)|Přehled zásad správy verzí rozhraní .NET Framework.|
|[Umístění sestavení](../../framework/app-domains/assembly-placement.md)|Kde lokalizovat sestavy.|
|[Sestavení a souběžné spouštění](side-by-side-execution.md)|Používejte více verzí runtime nebo sestavení současně.|
|[Generování dynamických metod a sestavení](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Jak vytvořit dynamická sestavení.|
|[Jak runtime vyhledá sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Jak rozhraní .NET Framework řeší odkazy na sestavení za běhu.|

## <a name="reference"></a>Referenční informace

<xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>Viz také

- [Formát souboru sestavení rozhraní .NET](file-format.md)
- [Přátelská sestavení](friend.md)
- [Referenční sestavení](reference-assemblies.md)
- [Postup: Načtení a uvolnění sestavení](load-unload.md)
- [Postup: Použití a ladění použitelnosti sestavení v rozhraní .NET Core](unloadability.md)
- [Postup: Určení, zda je soubor sestavením](identify.md)
