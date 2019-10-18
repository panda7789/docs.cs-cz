---
title: Analyzovat závislosti na kód portu pro .NET Core
description: Naučte se analyzovat externí závislosti, abyste mohli přenést projekt z .NET Framework do .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 36d1c1d2090a0fb9e6f48fe519d15897579df2d5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521469"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>Analyzovat závislosti na kód portu pro .NET Core

Chcete-li svůj kód přenést do rozhraní .NET Core nebo .NET Standard, je nutné pochopit závislosti. Externí závislosti jsou [balíčky NuGet](#analyze-referenced-nuget-packages-in-your-projects) nebo [knihovny DLL](#analyze-dependencies-that-arent-nuget-packages) , na které odkazujete v projektu, ale nebudete je sestavovat. Vyhodnoťte každou závislost a vytvořte pohotovostní plán pro ty, které nejsou kompatibilní s .NET Core. Tady je postup, jak zjistit, jestli je závislost kompatibilní s .NET Core.

## <a name="analyze-referenced-nuget-packages-in-your-projects"></a>Analyzovat odkazované balíčky NuGet ve vašich projektech

Pokud odkazujete na balíčky NuGet v projektu, musíte ověřit, jestli jsou kompatibilní s .NET Core.
Existují dva způsoby, jak to provést:

- [Použití aplikace Průzkumník balíčků NuGet](#analyze-nuget-packages-using-nuget-package-explorer)
- [Používání webu nuget.org](#analyze-nuget-packages-using-nugetorg)

Pokud nejsou po analýze balíčků kompatibilní s .NET Core a pouze cílovými .NET Framework, můžete zjistit, zda [.NET Framework režim kompatibility](#net-framework-compatibility-mode) může pomáhat s vaším procesem přenosu.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analýza balíčků NuGet pomocí Průzkumníka balíčků NuGet

Balíček NuGet je sada složek, které obsahují sestavení specifická pro konkrétní platformu. Proto je nutné ověřit, zda existuje složka, která obsahuje kompatibilní sestavení v rámci balíčku.

Nejjednodušší způsob, jak zkontrolovat složky balíčku NuGet, je použít nástroj [Průzkumník balíčků NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) . Po instalaci použijte následující postup k zobrazení názvů složek:

1. Otevřete Průzkumníka balíčků NuGet.
2. Klikněte na **Otevřít balíček z online informačního kanálu**.
3. Vyhledejte název balíčku.
4. Ve výsledcích hledání vyberte název balíčku a klikněte na **otevřít**.
5. Rozbalte složku *lib* na pravé straně a podívejte se na názvy složek.

Vyhledejte složku s některým z následujících názvů:

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
netcoreapp2.1
netcoreapp2.2
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Tyto hodnoty jsou [cílové monikery rozhraní .NET Framework (TFM)](../../standard/frameworks.md) , které jsou namapovány na verze [.NET Standard](../../standard/net-standard.md), .NET Core a tradiční profily PŘENOSITELNÉ knihovny tříd (PCL), které jsou kompatibilní s .NET Core.

> [!IMPORTANT]
> Při prohlížení TFM, který balíček podporuje, pamatujte, že `netcoreapp*`, i když je kompatibilní, je jenom pro projekty .NET Core, a ne pro .NET Standard projekty.
> Knihovna, která cílí jenom na `netcoreapp*` a ne `netstandard*`, může být spotřebovaná jenom jinými aplikacemi .NET Core.

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analýza balíčků NuGet pomocí nuget.org

Případně se můžete podívat na TFM, který každý balíček podporuje v [NuGet.org](https://www.nuget.org/) v části **závislosti** stránky balíčku.

I když použití webu je jednodušší způsob, jak ověřit kompatibilitu, informace o **závislostech** nejsou v lokalitě k dispozici pro všechny balíčky.

### <a name="net-framework-compatibility-mode"></a>Režim kompatibility .NET Framework

Po analýze balíčků NuGet můžete zjistit, že cílí jenom na .NET Framework jako většina balíčků NuGet.

Počínaje .NET Standard 2,0 byl zaveden režim kompatibility .NET Framework. Tento režim kompatibility umožňuje projektům .NET Standard a .NET Core odkazovat na .NET Framework knihovny. Odkazování na knihovny .NET Framework nefunguje pro všechny projekty, například pokud knihovna používá rozhraní API Windows Presentation Foundation (WPF), ale odblokuje mnoho scénářů přenosu.

Při odkazování na balíčky NuGet, které cílí na .NET Framework ve vašem projektu, jako je například [Huitian. PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), získáte upozornění záložního balíčku ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) podobně jako v následujícím příkladu:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Toto upozornění se zobrazí, když přidáte balíček a pokaždé, když ho sestavíte, abyste se ujistili, že balíček otestujete s vaším projektem. Pokud projekt pracuje podle očekávání, můžete toto upozornění potlačit úpravou vlastností balíčku v aplikaci Visual Studio nebo ruční úpravou souboru projektu ve svém oblíbeném editoru kódu.

Chcete-li potlačit upozornění úpravou souboru projektu, vyhledejte položku `PackageReference` balíčku, pro který chcete upozornění potlačit, a přidejte atribut `NoWarn`. Atribut `NoWarn` přijímá čárkami oddělený seznam všech ID upozornění. Následující příklad ukazuje, jak potlačit upozornění `NU1701` pro balíček `Huitian.PowerCollections` úpravou souboru projektu ručně:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Další informace o potlačení upozornění kompilátoru v aplikaci Visual Studio naleznete v tématu [potlačení upozornění pro balíčky NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).

## <a name="port-your-packages-to-packagereference"></a>Portování balíčků pro `PackageReference`

.NET Core používá [PackageReference](/nuget/consume-packages/package-references-in-project-files) k určení závislostí balíčku. Pokud k určení balíčků používáte [Package. config](/nuget/reference/packages-config) , budete muset převést na `PackageReference`.

Další informace najdete na adrese [migrace ze souboru Packages. config na PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Co dělat, když se závislost balíčku NuGet nespustí v .NET Core

Existuje několik věcí, které můžete udělat, pokud balíček NuGet, na kterém závisíte, neběží na .NET Core:

1. Pokud je projekt Open Source a hostovaný někde jako GitHub, můžete vývojáře přímo zapojit.
2. Autora můžete kontaktovat přímo na [NuGet.org](https://www.nuget.org/). Vyhledejte balíček a na levé straně stránky balíčku klikněte na **vlastníci kontaktní** osoby.
3. Můžete vyhledat jiný balíček, který běží v .NET Core, který provede stejnou úlohu jako balíček, který jste používali.
4. Můžete se pokusit napsat kód, který balíček prováděl sami.
5. Závislost na balíčku můžete eliminovat tak, že změníte funkčnost vaší aplikace alespoň do chvíle, kdy bude k dispozici kompatibilní verze balíčku.

Pamatujte na to, že open source projekty údržba a vydavatelé balíčků NuGet jsou často dobrovolníkem. Přispívají vzhledem k tomu, že se na danou doménu zajímá, je to zdarma a často mají jinou denní úlohu. Nezapomeňte to mít na vědomí, že při kontaktování s žádostí o podporu .NET Core.

Pokud nemůžete problém vyřešit pomocí některé z výše uvedených verzí, možná budete muset přenést na rozhraní .NET Core později.

Tým .NET by chtěl zjistit, které knihovny jsou pro podporu rozhraní .NET Core nejdůležitější. Můžete odeslat e-mail dotnet@microsoft.com o knihovnách, které chcete použít.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analyzovat závislosti, které nejsou balíčky NuGet

Může se jednat o závislost, která není balíčkem NuGet, jako je například knihovna DLL v systému souborů. Jediným způsobem, jak určit přenositelnost této závislosti, je spustit nástroj [analyzátor přenositelnosti .NET](https://github.com/Microsoft/dotnet-apiport) . Nástroj může analyzovat sestavení, která cílí na .NET Framework, a identifikovat rozhraní API, která nejsou přenosné na jiné platformy .NET, jako je .NET Core. Nástroj můžete spustit jako konzolovou aplikaci nebo jako [rozšíření sady Visual Studio](../../standard/analyzers/portability-analyzer.md).

>[!div class="step-by-step"]
>[Next](libraries.md)
