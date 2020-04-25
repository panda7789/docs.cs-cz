---
title: Přizpůsobení z .NET Framework na .NET Core
description: Pochopení procesu přenosu a zjišťování nástrojů, které můžete najít užitečné při přenosu .NET Framework projektu do .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: c6797a5b3a97ddd01f86498d896e859baf8997be
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158280"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>Přehled přenosů z .NET Framework do .NET Core

Je možné, že máte kód, který se v současnosti spouští na .NET Framework, které vás zajímá o přenos do .NET Core. Tento článek obsahuje:

* Přehled procesu přenosu.
* Seznam nástrojů, které můžete najít užitečné při přenosu kódu do .NET Core.

## <a name="overview-of-the-porting-process"></a>Přehled procesu přenosu

Přenos na rozhraní .NET Core (nebo .NET Standard) z .NET Framework pro mnoho projektů je relativně rovnou dopředně. Je potřeba provést několik změn, ale mnoho z nich se řídí vzorem popsaným níže. Projekty, ve kterých je model aplikace dostupný v .NET Core (například knihovny, konzolové aplikace a aplikace klasické pracovní plochy), obvykle vyžadují malé změny. Projekty, které vyžadují nový aplikační model, jako je například přesun do ASP.NET Core z ASP.NET, vyžadují trochu větší práci, ale mnoho vzorů má analogické, které lze použít při převodu. Tento dokument by měl pomáhat s určením hlavních strategií, které byly zaměstnány uživateli, aby úspěšně převedli své základy kódu na cílovou .NET Standard nebo .NET Core a převádějí na převod na dvou úrovních: specifické pro řešení a specifické pro projekt. Pokyny pro převody specifické pro model aplikace najdete v odkazech dole.

Při přenosu projektu do .NET Core doporučujeme použít následující postup. Každý z těchto kroků zavádí potenciální místa pro změny chování, takže před pokračováním v pozdějších krocích ověřte, zda je vaše knihovna nebo aplikace vhodně testována. Prvním postupem je příprava projektu na přepnutí do .NET Standard nebo .NET Core. Pokud máte testy jednotek, je nejlepší je nejdříve převést, abyste mohli pokračovat v testování změn v produktu, na kterém pracujete. Vzhledem k tomu, že přenos do .NET Core je taková významná změna vašeho základu kódu, důrazně doporučujeme přenést testovací projekty, abyste mohli spustit testy během přenosu kódu. MSTest, xUnit a NUnit všechny fungují na .NET Core.

## <a name="getting-started"></a>Začínáme

V celém procesu se budou používat tyto nástroje:

- Visual Studio 2019
- Stáhnout [analyzátor přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md)
- _Volitelné_ Instalace příkazu [dotnet try-Convert](https://github.com/dotnet/try-convert)

## <a name="porting-a-solution"></a>Portování řešení

V případě, že existuje více projektů v řešení, může být přenos složitější, protože je nutné adresovat projekty v určitém pořadí. Proces převodu by měl být v rámci nejnižšího přístupu, kde se nejprve převádějí projekty bez závislostí na jiných projektech v řešení a pokračuje v celém řešení.

Chcete-li identifikovat projekty objednávek, které by měly být migrovány, můžete použít následující nástroje:

- [Diagramy závislostí v aplikaci Visual Studio](/visualstudio/modeling/create-layer-diagrams-from-your-code) mohou vytvořit orientovaný graf kódu v řešení.
- Spusťte `msbuild _SolutionPath_ /t:GenerateRestoreGraphFile /p:RestoreGraphOutputPath=graph.dg.json` pro vygenerování dokumentu JSON, který obsahuje seznam odkazů projektu.

## <a name="per-project-steps"></a>Podle kroků projektu

Při přenosu projektu do .NET Core doporučujeme použít následující postup:

1. Převeďte všechny vaše `packages.config` závislosti na formát [PackageReference](/nuget/consume-packages/package-references-in-project-files) pomocí nástroje pro [převod v aplikaci Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).

   Tento krok zahrnuje převod závislostí ze starší verze `packages.config` formátu. `packages.config`nefunguje na .NET Core, takže tento převod je nutný, pokud máte závislosti balíčku. Vyžaduje taky jenom závislosti, které přímo používáte v projektu, což usnadňuje pozdější kroky snížením počtu závislostí, které musíte spravovat.

1. Převeďte soubor projektu na novou strukturu souborů ve stylu sady SDK. Můžete vytvořit nové projekty pro .NET Core a kopírovat přes zdrojové soubory nebo se pokusit převést existující soubor projektu pomocí nástroje.

   .NET Core používá zjednodušený (a odlišný) [Formát souboru projektu](../tools/csproj.md) než .NET Framework. Aby bylo možné pokračovat, budete muset soubory projektu převést do tohoto formátu. Tento styl projektu umožňuje také cílit .NET Framework, které v tuto chvíli budete chtít i nadále cílit.

   Můžete se pokusit o port menší řešení nebo jednotlivé projekty v jedné operaci do formátu souboru projektu .NET Core pomocí nástroje [dotnet try-Convert](https://github.com/dotnet/try-convert) . `dotnet try-convert`není zaručená práce pro všechny vaše projekty a může způsobit drobné změny v chování, které jste v závislosti na. Použijte ho jako _výchozí bod_ , který automatizuje základní věci, které je možné automatizovat. Není zaručeným řešením pro migraci projektu, protože jsou v porovnání s původními soubory projektu sady SDK k dispozici mnoho rozdílů v cílech používaných projekty stylu sady SDK.

1. Přecílíte na všechny projekty, které chcete přenést na cílovou .NET Framework 4.7.2 nebo vyšší.

   Tento krok zajistí, že můžete použít alternativy rozhraní API pro cíle specifické pro .NET Framework, když .NET Core nepodporuje konkrétní rozhraní API.

1. Aktualizujte všechny závislosti na nejnovější verzi. Projekty mohou používat starší verze knihoven, které nemusí mít .NET Standard podporu. Novější verze je však může podporovat pomocí jednoduchého přepínače. To může vyžadovat změny kódu, pokud dojde k zásadním změnám v knihovnách.

1. Pomocí [analyzátoru přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) můžete analyzovat vaše sestavení a zjistit, jestli jsou přenosné do .NET Core.

   Nástroj Analyzátor přenositelnosti .NET analyzuje vaše kompilovaná sestavení a generuje sestavu. Tato sestava zobrazuje souhrn přenositelnosti na vysoké úrovni a rozdělení každého rozhraní API, které používáte, není k dispozici v rozhraní .NET Core. Při používání tohoto nástroje odešlete pouze jednotlivé projekty, které převádíte, abyste se mohli zaměřit na změny rozhraní API, které jsou potenciálně nutné. Mnoho rozhraní API má ekvivalentní dostupnost v rozhraní .NET Core, na kterou chcete přejít.

   Při čtení sestav vygenerovaných analyzátorem jsou důležité informace skutečná rozhraní API, která se používají, a ne nutně procento podpory cílové platformy. Mnoho rozhraní API má v .NET Standard/Core stejné možnosti, a proto je potřeba pochopit, jaké scénáře vaše knihovna nebo aplikace potřebuje rozhraní API, aby bylo možné určit, že se má přenositelnost vynásobit.

   Existují některé případy, kdy rozhraní API nejsou ekvivalentní a je třeba provést některé direktivy preprocesoru kompilátoru (tj. `#if NET45`) na speciální případ platforem. V tomto okamžiku bude projekt stále cílen .NET Framework. U každého z těchto cílových případů se doporučuje použít známé podmíněné výrazy, které lze chápat jako scénář.  Například podpora AppDomain v .NET Core je omezená, ale pro scénář načítání a uvolňování sestavení existuje nové rozhraní API, které není k dispozici v rozhraní .NET Core. Běžný způsob, jak to zpracovat v kódu, by byl podobný:

   ```csharp
   #if FEATURE_APPDOMAIN_LOADING
   // Code that uses appdomains
   #elif FEATURE_ASSEMBLY_LOAD_CONTEXT
   // Code that uses assembly load context
   #else
   #error Unsupported platform
   #endif
   ```

1. Nainstalujte do svých projektů [analyzátor rozhraní .NET API](../../standard/analyzers/api-analyzer.md) a Identifikujte rozhraní API <xref:System.PlatformNotSupportedException> , která se vyvolávají na některých platformách a nějaké jiné potenciální problémy s kompatibilitou.

   Tento nástroj je podobný analyzátoru přenositelnosti, ale místo analýzy, jestli se kód může sestavovat v .NET Core, analyzuje, jestli používáte rozhraní API způsobem, který zavolá <xref:System.PlatformNotSupportedException> v době běhu. I když se nejedná o běžný postup, Pokud přesouváte z .NET Framework 4.7.2 nebo vyšší, je dobré ho kontrolovat. Další informace o rozhraních API, která vyvolávají výjimky v rozhraní .NET Core, najdete v tématu [rozhraní API, která vždy vyvolají výjimky v rozhraní .NET Core](../compatibility/unsupported-apis.md).

1. V tomto okamžiku se můžete přepnout na cílení na .NET Core (obecně pro aplikace) nebo .NET Standard (pro knihovny).

   Volba mezi .NET Core a .NET Standard je převážně závislá na tom, kde se projekt spustí. Pokud se jedná o knihovnu, kterou budou používat jiné aplikace nebo distribuované přes NuGet, je obvykle vhodné cílit na .NET Standard. Existují však rozhraní API, která jsou k dispozici pouze v rozhraní .NET Core pro výkon nebo jiné důvody. v takovém případě by mělo být rozhraní .NET Core cíleno na potenciálně .NET Standard sestavení i na nižší výkon a funkčnost. Když cílíte .NET Standard, projekt bude připravený ke spuštění na nových platformách (například WebAssembly). Pokud projekt obsahuje závislosti na konkrétních aplikačních architekturách (například ASP.NET Core), bude cíl omezen tím, co podporují závislosti.

   Pokud neexistují žádné direktivy preprocesoru pro podmíněný kód kompilace pro .NET Framework nebo .NET Standard, bude to jednoduché, jak najít následující v souboru projektu:

   ```xml
   <TargetFramework>net472</TargetFramework>
   ```

   a přepněte ho do požadovaného rozhraní. Pro .NET Core 3,1 to bude:

   ```xml
   <TargetFramework>netcoreapp3.1</TargetFramework>
   ```

   Pokud se však jedná o knihovnu, pro kterou chcete pokračovat v podpoře .NET Frameworkch specifických sestavení, můžete [více cílit](../../standard/library-guidance/cross-platform-targeting.md) tím, že je nahradíte následujícími:

   ```xml
   <TargetFrameworks>net472;netstandard2.0</TargetFrameworks>
   ```

   Pokud používáte rozhraní API specifická pro systém Windows (například přístup do registru), nainstalujte [sadu Windows Compatibility Pack](./windows-compat-pack.md).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Analyze dependencies](third-party-deps.md)
> ASP.NET migrace balíčku[NuGet](../deploying/creating-nuget-packages.md)
> balíčku závislostí[na ASP.NET Core](/aspnet/core/migration/proper-to-2x)
