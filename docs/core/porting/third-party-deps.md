---
title: Analýza závislostí na kód portu na jádro rozhraní .NET Core
description: Zjistěte, jak analyzovat externí závislosti za účelem přenosu projektu z rozhraní .NET Framework na jádro .NET.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 2aa09e551a99358d3a6961fafcfc0aa8dbd976b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398963"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>Analýza závislostí na kód portu na jádro rozhraní .NET Core

Chcete-li přenést kód do rozhraní .NET Core nebo .NET Standard, musíte pochopit vaše závislosti. Externí závislosti jsou balíčky `.dll` NuGet nebo soubory, na které odkazujete v projektu, ale které sami nevytvoříte.

## <a name="migrate-your-nuget-packages-to-packagereference"></a>Migrujte balíčky NuGet do`PackageReference`

Jádro .NET používá [PackageReference](/nuget/consume-packages/package-references-in-project-files) k určení závislostí balíčků. Pokud používáte [packages.config](/nuget/reference/packages-config) k určení balíčků v projektu, `PackageReference` převeďte `packages.config` je do formátu, protože není podporován v .NET Core.

Informace o migraci naleznete v článku [Migrace z packages.config do packagereference.](/nuget/reference/migrate-packages-config-to-package-reference)

## <a name="upgrade-your-nuget-packages"></a>Upgrade balíčků NuGet

Po migraci projektu `PackageReference` do formátu ověřte, zda jsou balíčky kompatibilní s rozhraním .NET Core.

Nejprve upgradujte balíčky na nejnovější verzi, kterou můžete. To lze provést pomocí ui Správce balíčků NuGet v sadě Visual Studio. Je pravděpodobné, že novější verze závislostí balíčků jsou již kompatibilní s rozhraním .NET Core.

## <a name="analyze-your-package-dependencies"></a>Analýza závislostí balíčků

Pokud jste ještě neověřili, že vaše převedené a upgradované závislosti balíčků fungují na jádru .NET, existuje několik způsobů, jak toho dosáhnout:

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analýza balíčků NuGet pomocí nuget.org

Můžete vidět cílové framework zástupné názvy (TFM), které každý balíček podporuje na [nuget.org](https://www.nuget.org/) v části **Závislosti** na stránce balíčku.

Přestože použití webu je jednodušší způsob ověření **kompatibility,** informace o závislostech nejsou na webu k dispozici pro všechny balíčky.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analýza balíčků NuGet pomocí Aplikace NuGet Package Explorer

Balíček NuGet je sama o sobě sada složek, které obsahují sestavení specifické pro platformu. Zkontrolujte, zda je složka, která obsahuje kompatibilní sestavení uvnitř balíčku.

Nejjednodušší způsob, jak zkontrolovat složky balíčku NuGet je použít nástroj [NuGet Package Explorer.](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) Po instalaci zotente názvy složek pomocí následujících kroků:

1. Otevřete Průzkumník balíčků NuGet.
2. Klikněte na **Otevřít balíček z online kanálu**.
3. Vyhledejte název balíčku.
4. Ve výsledcích hledání vyberte název balíčku a klepněte na **tlačítko otevřít**.
5. Rozbalte složku *lib* na pravé straně a podívejte se na názvy složek.

Vyhledejte složku s názvy pomocí jednoho `netstandardX.Y` `netcoreappX.Y`z následujících vzorů: nebo .

Tyto hodnoty jsou [zástupné názvy target framework (TFM),](../../standard/frameworks.md) které jsou mapovány na verze profilů [.NET Standard](../../standard/net-standard.md), .NET Core a tradiční knihovny přenosných tříd (PCL), které jsou kompatibilní s rozhraním .NET Core.

> [!IMPORTANT]
> Při pohledu na TFM, které balíček podporuje, všimněte si, že `netcoreapp*`, zatímco kompatibilní, je pouze pro projekty .NET Core a ne pro projekty .NET Standard.
> Knihovna, která `netcoreapp*` cílí pouze a ne `netstandard*` může být spotřebována pouze jinými aplikacemi .NET Core.

## <a name="net-framework-compatibility-mode"></a>Režim kompatibility rozhraní .NET Framework

Po analýze nuget balíčky, můžete zjistit, že se zaměřují pouze na rozhraní .NET Framework.

Počínaje rozhraním .NET Standard 2.0 byl zaveden režim kompatibility rozhraní .NET Framework. Tento režim kompatibility umožňuje projektům .NET Standard a .NET Core odkazovat na knihovny rozhraní .NET Framework. Odkazování na knihovny rozhraní .NET Framework nefunguje pro všechny projekty, například pokud knihovna používá rozhraní API Windows Presentation Foundation (WPF), ale odblokuje mnoho scénářů přenosu.

Když odkazujete na balíčky NuGet, které cílí na rozhraní .NET Framework v projektu, například [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), zobrazí se záložní upozornění balíčku ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) podobné následujícímu příkladu:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Toto upozornění se zobrazí při přidání balíčku a pokaždé, když vytvoříte, abyste se ujistili, že testujete tento balíček s projektem. Pokud váš projekt funguje podle očekávání, můžete potlačit toto upozornění úpravou vlastností balíčku v sadě Visual Studio nebo ruční úpravou souboru projektu v oblíbeném editoru kódu.

Chcete-li potlačit upozornění úpravou souboru `PackageReference` projektu, vyhledejte položku pro balíček, pro který chcete upozornění potlačit, a přidejte `NoWarn` atribut. Atribut `NoWarn` přijímá seznam všech ID upozornění oddělených čárkami. Následující příklad ukazuje, jak `NU1701` potlačit `Huitian.PowerCollections` upozornění pro balíček ruční úpravou souboru projektu:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Další informace o tom, jak potlačit upozornění kompilátoru v sadě Visual Studio, naleznete [v tématu Potlačení upozornění pro balíčky NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Co dělat, když se závislost balíčku NuGet nespustí na jádru .NET Core

Existuje několik věcí, které můžete udělat, pokud balíček NuGet, na který jste závislí, neběží na .NET Core:

- Pokud je projekt open source a hostuje někde jako GitHub, můžete zapojit vývojáře přímo.
- Můžete kontaktovat autora přímo na [nuget.org](https://www.nuget.org/). Vyhledejte balíček a klikněte na **kontakt vlastníci** na levé straně stránky balíčku.
- Můžete vyhledat jiný balíček, který běží na .NET Core, který provádí stejný úkol jako balíček, který jste používali.
- Můžete se pokusit napsat kód balíček dělal sami.
- Závislost na balíčku můžete eliminovat změnou funkčnosti aplikace, alespoň dokud nebude k dispozici kompatibilní verze balíčku.

Nezapomeňte, že správci open source projektu a vydavatelé balíčků NuGet jsou často dobrovolníci. Přispívají, protože se starají o danou doménu, dělají to zdarma a často mají jinou denní práci. Mějte na paměti, že při kontaktování je požádat o podporu .NET Core.

Pokud nemůžete vyřešit problém s některou z těchto možností, bude pravděpodobně muset port na .NET Core později.

Tým .NET by chtěl vědět, které knihovny jsou nejdůležitější pro podporu s .NET Core. Knihovnám, které dotnet@microsoft.com chcete použít, můžete poslat e-mail.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analýza závislostí, které nejsou balíčky NuGet

Můžete mít závislost, která není balíček NuGet, jako je například DLL v systému souborů. Jediným způsobem, jak určit přenositelnost této závislosti, je spuštění nástroje [.NET Portability Analyzer.](https://github.com/Microsoft/dotnet-apiport) Nástroj analyzuje sestavení, která cílí na rozhraní .NET Framework, a identifikuje rozhraní API, která nejsou přenosná na jiné platformy .NET, například .NET Core. Nástroj můžete spustit jako konzolovou aplikaci nebo jako [rozšíření sady Visual Studio](../../standard/analyzers/portability-analyzer.md).

## <a name="next-steps"></a>Další kroky

>[!div class="nextstepaction"]
>[Přenos knihoven](libraries.md)
