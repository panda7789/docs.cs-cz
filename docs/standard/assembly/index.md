---
title: Sestavení v rozhraní .NET
ms.date: 07/10/2018
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
---
# <a name="assemblies-in-net"></a>Sestavení v rozhraní .NET

Tvoří základní jednotku nasazení, správu verzí, opětovného použití, rozsahu platnosti při aktivaci a oprávnění zabezpečení pro sestavení. Aplikace založené na síť. Sestavení podobu spustitelný soubor (.exe) nebo soubor dynamické knihovny (.dll) a jsou stavební bloky aplikací rozhraní .NET. Modul common language runtime poskytují informace, musí se jednat o seznámen typu implementace. Si můžete představit jako kolekce typů a prostředků, které tvoří logickou jednotku funkčnosti a jsou sestaveny vzájemnou spolupráci sestavení.

V .NET Core a .NET Framework sestavení se dají ze jeden nebo více souborů zdrojového kódu. V rozhraní .NET Framework sestavení může obsahovat jeden nebo více modulů. Díky tomu větší projekty ji naplánovat tak, že několik jednotliví vývojáři práci v samostatných souborech zdrojového kódu nebo moduly, které se spojí dohromady a vytvoří jednoho sestavení. Další informace o modulech najdete v tématu [jak: Vytváření vícesouborového sestavení](../../framework/app-domains/how-to-build-a-multifile-assembly.md).

Sestavení mají následující vlastnosti:

- Sestavení se implementují jako soubory .exe nebo .dll.

- Pro knihovny cílené na rozhraní .NET Framework, můžete sdílet sestavení mezi aplikacemi tak, že vložíte ho [globální mezipaměti sestavení](../../framework/app-domains/gac.md). Sestavení musí být silným názvem předtím, než mohou být součástí globální mezipaměti sestavení. Další informace najdete v tématu [sestavení se silným názvem](../../framework/app-domains/strong-named-assemblies.md).

- Sestavení jsou načtena do paměti pouze pokud jsou požadována. Pokud nejsou použity, nejsou načtené. To znamená, že sestavení mohou být účinný způsob, jak spravovat prostředky ve větších projektů.

- Informace o sestavení můžete získat prostřednictvím kódu programu pomocí reflexe. Další informace najdete v tématu [reflexe (C#)](../../csharp/programming-guide/concepts/reflection.md) nebo [reflexe (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Můžete načíst sestavení pouze chcete zkontrolovat voláním metody <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>.

## <a name="assembly-manifest"></a>Manifest sestavení

V rámci každé sestavení je *manifestu sestavení*. Podobně jako obsah, manifest sestavení obsahuje následující:

- Identita sestavení (jeho název a verzi).

- Soubor tabulku popisující všechny ostatní soubory, které tvoří sestavení, jako je například jiné sestavení, který jste vytvořili, že váš soubor .exe nebo .dll se může spolehnout, nebo dokonce rastrový obrázek nebo soubory Readme.

- *Seznam odkazů sestavení*, což je seznam všech externích závislostí – knihovny DLL debuggle nebo jiné soubory potřeby vaší aplikace, které byla pravděpodobně vytvořena jiným uživatelem. Odkazy na sestavení obsahují odkazy na globální i soukromá objekty. Globální objekty jsou k dispozici pro všechny ostatní aplikace. V .NET Core jsou svázány s konkrétním modulem runtime .NET Core. V rozhraní .NET Framework kde se nacházejí v globální mezipaměti sestavení. <xref:System.IO?displayProperty=nameWithType> Obor názvů je příkladem sestavení v globální mezipaměti sestavení. Soukromé objekty musí být v adresáři na buď stejné úrovni jako nebo adresáři, ve kterém je nainstalována aplikace.

Protože sestavení obsahují informace o obsahu, správy verzí a závislostech, aplikace, které je používají nemusí spoléhat na hodnoty registru Windows fungovat správně. Sestavení omezit konflikty DLL a spolehlivější a usnadňuje nasazení, aby byly vaše aplikace. V mnoha případech můžete nainstalovat. Aplikace založené na NET jednoduše tak, že kopírováním jeho souborů k cílovému počítači. Další informace najdete v tématu [Manifest sestavení](../../framework/app-domains/assembly-manifest.md).

## <a name="adding-a-reference-to-an-assembly"></a>Přidání odkazu na sestavení

Pokud chcete použít sestavení, musíte přidat odkaz na ni. V dalším kroku můžete použít [direktiva using](../../csharp/language-reference/keywords/using-directive.md) pro C# nebo [Imports – příkaz](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) v jazyce Visual Basic zvolte obor názvů položek, které chcete použít. Po sestavení odkazuje a importovat, všechny dostupné typy, vlastnosti, metody a ostatní členy jeho obory názvů jsou k dispozici pro vaši aplikaci jako kdyby byly jejich kód částí zdrojového souboru.

> [!NOTE]
> Většina z knihovny tříd .NET se reference na sestavení automaticky. V některých případech se však o systémové sestavení nemusí automaticky odkazovat. V .NET Core, můžete přidat odkaz na balíček NuGet, který obsahuje sestavení s použitím Správce balíčků NuGet v sadě Visual Studio nebo přidáním [ \<PackageReference >](../../core/tools/dependencies.md#the-new-packagereference-element) – element pro sestavení *.csproj nebo *.vbproj projektu. V rozhraní .NET Framework, můžete přidat odkaz na sestavení pomocí **přidat odkaz** dialogového okna v sadě Visual Studio nebo pomocí `-reference` možnost příkazového řádku pro [ C# ](../../csharp/language-reference/compiler-options/reference-compiler-option.md) nebo [ Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) kompilátory.

V jazyce C# můžete také použít dvě verze téhož sestavení se v jedné aplikaci. Další informace najdete v tématu [externí alias](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="creating-an-assembly"></a>Vytváření sestavení

Zkompilujte aplikaci sestavením v sadě Visual Studio podle sestavení z příkazového řádku s použitím rozhraní příkazového řádku (CLI) nástroje .NET Core nebo vytvořením sestavení rozhraní .NET Framework pomocí příkazového řádku kompilátoru. Další informace o vytváření sestavení pomocí nástrojů rozhraní příkazového řádku .NET najdete v tématu [nástroje rozhraní příkazového řádku (CLI) pro .NET Core](../../core/tools/index.md). Vytváření sestavení pomocí kompilátoru příkazového řádku, naleznete v tématu [sestavení z příkazového řádku s csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) pro C# a [sestavení z příkazového řádku](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) v jazyce Visual Basic.

> [!NOTE]
> K vytvoření sestavení v sadě Visual Studio na **sestavení** nabídku zvolte **sestavení**.

## <a name="see-also"></a>Viz také:

- [Formát souborů sestavení .NET](file-format.md)
- [Sestavení v modulu CLR (Common Language Runtime)](../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Přátelská sestavení](friend-assemblies.md)
- [Postupy: Zavedení a uvolnění sestavení (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Postupy: Zavedení a uvolnění sestavení (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Postupy: Použití a ladění funkce zrušení načtení sestavení v .NET Core](unloadability-howto.md)
- [Postupy: Určení, zda je soubor sestavení (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
- [Postupy: Určení, zda je soubor sestavení (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
