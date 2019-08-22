---
title: Sestavení v .NET
ms.date: 07/10/2018
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
ms.openlocfilehash: 09dc44141a4eea7601df3f918e8740efdb99aeda
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666591"
---
# <a name="assemblies-in-net"></a>Sestavení v .NET

Sestavení tvoří základní jednotku nasazení, řízení verze, opětovné použití, rozsah aktivace a oprávnění zabezpečení pro. Aplikace založená na síti. Sestavení mají formu spustitelného souboru (. exe) nebo souboru dynamické knihovny (. dll) a jsou stavebními bloky aplikací .NET. Poskytují modul CLR (Common Language Runtime) s informacemi, které musí být vědomy typu implementace. Sestavení si můžete představit jako kolekci typů a prostředků, které tvoří logickou jednotku funkce a jsou sestaveny tak, aby společně spolupracovaly.

V rozhraní .NET Core a .NET Framework sestavení může být sestaveno z jednoho nebo více souborů zdrojového kódu. V .NET Framework sestavení mohou obsahovat jeden nebo více modulů. To umožňuje, aby se větší projekty naplánovaly takovým způsobem, že několik individuálních vývojářů pracuje na samostatných souborech zdrojového kódu nebo v modulech, které jsou kombinovány pro vytvoření jednoho sestavení. Další informace o modulech naleznete v [tématu How to: Sestavení vícesouborového sestavení](../../framework/app-domains/how-to-build-a-multifile-assembly.md).

Sestavení mají následující vlastnosti:

- Sestavení jsou implementována jako soubory. exe nebo. dll.

- Pro knihovny, které cílí na .NET Framework můžete sdílet sestavení mezi aplikacemi jejich vložením do [globální mezipaměti sestavení (GAC](../../framework/app-domains/gac.md)). Aby bylo možné zahrnout sestavení do globální mezipaměti sestavení (GAC), musí být sestavení silného názvu. Další informace naleznete v tématu [sestavení se silným názvem](../../framework/app-domains/strong-named-assemblies.md).

- Sestavení jsou načtena do paměti pouze v případě, že jsou požadována. Pokud se nepoužívají, nebudou načteny. To znamená, že sestavení mohou představovat efektivní způsob správy prostředků ve větších projektech.

- Můžete programově získat informace o sestavení pomocí reflexe. Další informace naleznete v tématu [Reflection (C#)](../../csharp/programming-guide/concepts/reflection.md) nebo [Reflection (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Sestavení lze načíst pouze pro kontrolu pomocí <xref:System.Reflection.MetadataLoadContext> třídy.

## <a name="assembly-manifest"></a>Manifest sestavení

V rámci každého sestavení je *manifest sestavení*. Podobně jako obsah, manifest sestavení obsahuje následující:

- Identita sestavení (jeho název a verze)

- Tabulka souborů popisující všechny ostatní soubory, které tvoří sestavení, například jiná sestavení, která jste vytvořili, aby soubor. exe nebo. dll spoléhá na soubory rastrového obrázku nebo souboru Readme.

- *Seznam odkazů na sestavení*, což je seznam všech vnějších závislostí –. dll nebo jiné soubory, které vaše aplikace potřebuje, aby mohla být vytvořena někým jiným. Odkazy na sestavení obsahují odkazy na globální i privátní objekty. Globální objekty jsou k dispozici pro všechny ostatní aplikace. V .NET Core jsou spojeny s konkrétním modulem runtime .NET Core. V .NET Framework se nachází v globální mezipaměti sestavení (GAC). <xref:System.IO?displayProperty=nameWithType> Obor názvů je příkladem sestavení v globální mezipaměti sestavení (GAC). Soukromé objekty musí být v adresáři na stejné úrovni, jako je adresář, ve kterém je nainstalována vaše aplikace.

Vzhledem k tomu, že sestavení obsahují informace o obsahu, správy verzí a závislostech, aplikace, které je používají, nemusí být závislé na hodnotách registru Windows, aby fungovaly správně. Sestavení snižují konflikty knihoven DLL a umožňují spolehlivější a snazší nasazení aplikací. V mnoha případech můžete nainstalovat. Pomocí čisté aplikace můžete jednoduše zkopírovat své soubory do cílového počítače. Další informace naleznete v tématu [manifest sestavení](../../framework/app-domains/assembly-manifest.md).

## <a name="adding-a-reference-to-an-assembly"></a>Přidání odkazu na sestavení

Chcete-li použít sestavení, je nutné přidat odkaz na něj. V dalším kroku můžete použít příkaz [using](../../csharp/language-reference/keywords/using-directive.md) pro C# nebo [Imports](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro Visual Basic k výběru oboru názvů položek, které chcete použít. Po odkazování na sestavení a importu všech dostupných typů, vlastností, metod a dalších členů svých oborů názvů jsou k dispozici pro vaši aplikaci, jako by jejich kód byl součástí zdrojového souboru.

> [!NOTE]
> Většina sestavení z knihovny tříd .NET je odkazována automaticky. V některých případech je však systémové sestavení pravděpodobně neodkazováno na automaticky. V rozhraní .NET Core můžete přidat odkaz na balíček NuGet, který obsahuje sestavení pomocí Správce balíčků NuGet v aplikaci Visual Studio nebo přidáním [ \<prvku PackageReference >](../../core/tools/dependencies.md#the-new-packagereference-element) pro sestavení do projektu *. csproj nebo *. vbproj. V .NET Framework můžete přidat odkaz na sestavení pomocí dialogového okna **Přidat odkaz** v aplikaci Visual Studio nebo pomocí `-reference` možnosti příkazového řádku pro kompilátory [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) nebo [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) .

V C#nástroji můžete použít také dvě verze stejného sestavení v jedné aplikaci. Další informace najdete v tématu [extern alias](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="creating-an-assembly"></a>Vytvoření sestavení

Zkompilujte aplikaci jejich sestavením v aplikaci Visual Studio, a to vytvořením z příkazového řádku pomocí nástrojů rozhraní příkazového řádku (CLI) .NET Core nebo sestavením .NET Framework sestavení pomocí kompilátoru příkazového řádku. Další informace o vytváření sestavení pomocí nástrojů rozhraní příkazového řádku .NET najdete v tématu [.NET Core Command-line interface (CLI) Tools](../../core/tools/index.md). Pro vytváření sestavení pomocí kompilátorů příkazového řádku, viz [sestavení příkazového řádku s CSc. exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) pro C# a sestavování [z příkazového řádku](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) pro Visual Basic.

> [!NOTE]
> Chcete-li sestavit sestavení v aplikaci Visual Studio, v nabídce **sestavení** klikněte na příkaz **sestavit**.

## <a name="see-also"></a>Viz také:

- [Formát souboru sestavení .NET](file-format.md)
- [Sestavení v modulu CLR (Common Language Runtime)](../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Přátelská sestavení](friend-assemblies.md)
- [Postupy: Načíst a uvolnit sestavení (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Postupy: Načíst a uvolnit sestavení (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Postupy: Použití a ladění funkce zrušení načtení sestavení v .NET Core](unloadability-howto.md)
- [Postupy: Určení, zda je soubor sestavením (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
- [Postupy: Určení, zda je soubor sestavením (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
