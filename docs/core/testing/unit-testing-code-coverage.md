---
title: Použití pokrytí kódu pro testování částí
description: Naučte se používat funkce pokrytí kódu pro testy jednotek .NET.
author: IEvangelist
ms.author: dapine
ms.date: 06/16/2020
ms.openlocfilehash: d19975283bf60e5cf3a9656c1b6f7966e12d2176
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105421"
---
# <a name="use-code-coverage-for-unit-testing"></a>Použití pokrytí kódu pro testování částí

Testování částí vám pomůžou zajistit funkčnost a poskytnout způsob ověřování pro úsilí refaktoringu. Pokrytí kódu je měření množství kódu, který je spouštěn testy jednotek – buď řádky, větve nebo metody. Příklad: Pokud máte jednoduchou aplikaci, která má pouze dvě podmíněné větve kódu (_větev a_, a _větev b_), testování částí, které ověřuje podmíněnou _větev a_ , bude mít za to, že pokrytí kódu větve a bude hlásit 50%.

Tento článek popisuje použití pokrytí kódu pro testování částí pomocí Coverlet a generování sestav pomocí ReportGenerator. I když se tento článek zaměřuje na C# a xUnit jako testovací rozhraní, budou fungovat i MSTest a NUnit. Coverlet je [Open source projekt na GitHubu](https://github.com/coverlet-coverage/coverlet) , který poskytuje architekturu pokrytí kódu pro různé platformy pro C#. [Coverlet](https://dotnetfoundation.org/projects/coverlet) je součástí .NET Foundation. Coverlet shromažďuje data testovacího běhu Cobertura, která se používají pro generování sestav.

Kromě toho tento článek podrobně popisuje, jak používat informace o pokrytí kódu shromážděné z testovacího běhu Coverlet k vygenerování sestavy. Generování sestav je možné pomocí jiného [Open source projektu na GitHub-ReportGenerator](https://github.com/danielpalme/ReportGenerator). ReportGenerator převádí sestavy pokrytí vygenerované Coberturami mezi mnoho dalších, a to v různých formátech v rámci lidských čitelných sestav.

## <a name="system-under-test"></a>Testovaný systém

"Testovaný systém" odkazuje na kód, u kterého píšete testy jednotek, může to být objekt, služba nebo cokoli jiného, co zpřístupňuje testovatelné funkce. Pro účely tohoto článku vytvoříte knihovnu tříd, která bude testovaným systémem, a dva odpovídající projekty testování částí.

### <a name="create-a-class-library"></a>Vytvoření knihovny tříd

Z příkazového řádku v novém adresáři s názvem `UnitTestingCodeCoverage` vytvořte novou knihovnu tříd .NET Standard pomocí [`dotnet new classlib`](../tools/dotnet-new.md#classlib) příkazu:

```dotnetcli
dotnet new classlib -n Numbers
```

Následující fragment kódu definuje jednoduchou `PrimeService` třídu, která poskytuje funkce pro kontrolu, zda je číslo typu primární. Zkopírujte následující fragment kódu a nahraďte obsah souboru *Class1.cs* , který byl automaticky vytvořen v adresáři *Numbers* . Přejmenujte soubor *Class1.cs* na *PrimeService.cs*.

```csharp
namespace System.Numbers
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            if (candidate < 2)
            {
                return false;
            }

            for (int divisor = 2; divisor <= Math.Sqrt(candidate); ++divisor)
            {
                if (candidate % divisor == 0)
                {
                    return false;
                }
            }
            return true;
        }
    }
}
```

> [!TIP]
> Stojí za zmínku o tom, že `Numbers` Knihovna tříd byla záměrně přidána do `System` oboru názvů. To umožňuje <xref:System.Math?displayProperty=fullName> , aby byla přístupná bez `using System;` deklarace oboru názvů. Další informace naleznete v tématu [Namespace (Referenční dokumentace jazyka C#)](../../csharp/language-reference/keywords/namespace.md).

### <a name="create-test-projects"></a>Vytváření projektů testů

Vytvořte dvě nové šablony **projektu XUnit test (.NET Core)** ze stejného příkazového řádku pomocí [`dotnet new xunit`](../tools/dotnet-new.md#test) příkazu:

```dotnetcli
dotnet new xunit -n XUnit.Coverlet.Collector
```

```dotnetcli
dotnet new xunit -n XUnit.Coverlet.MSBuild
```

Oba nově vytvořené projekty testů xUnit musí přidat odkaz na projekt třídy *Numbers* Library. To je tak, že testovací projekty mají přístup k *PrimeService* k testování. Z příkazového řádku použijte [`dotnet add`](../tools/dotnet-add-reference.md) příkaz:

```dotnetcli
dotnet add XUnit.Coverlet.Collector\XUnit.Coverlet.Collector.csproj reference Numbers\Numbers.csproj
```

```dotnetcli
dotnet add XUnit.Coverlet.MSBuild\XUnit.Coverlet.MSBuild.csproj reference Numbers\Numbers.csproj
```

Projekt *MSBuild* se jmenuje vhodně, jak bude záviset na balíčku NuGet [coverlet. MSBuild](https://www.nuget.org/packages/coverlet.msbuild) . Tuto závislost balíčku přidejte spuštěním [`dotnet add package`](../tools/dotnet-add-package.md) příkazu:

```dotnetcli
cd XUnit.Coverlet.MSBuild && dotnet add package coverlet.msbuild && cd ..
```

Předchozí příkaz v adresáři efektivně změnil obor na projekt testů *MSBuild* a pak přidal balíček NuGet. Až to bude hotové, změnily se adresáře a prohloubí se o jednu úroveň výš.

Otevřete oba soubory *UnitTest1.cs* a nahraďte jejich obsah následujícím fragmentem kódu. Přejmenujte soubory *UnitTest1.cs* na *PrimeServiceTests.cs*.

```csharp
using System.Numbers;
using Xunit;

namespace XUnit.Coverlet
{
    public class PrimeServiceTests
    {
        readonly PrimeService _primeService;

        public PrimeServiceTests() => _primeService = new PrimeService();

        [
            Theory,
            InlineData(-1), InlineData(0), InlineData(1)
        ]
        public void IsPrime_ValuesLessThan2_ReturnFalse(int value) =>
            Assert.False(_primeService.IsPrime(value), $"{value} should not be prime");

        [
            Theory,
            InlineData(2), InlineData(3), InlineData(5), InlineData(7)
        ]
        public void IsPrime_PrimesLessThan10_ReturnTrue(int value) =>
            Assert.True(_primeService.IsPrime(value), $"{value} should be prime");

        [
            Theory,
            InlineData(4), InlineData(6), InlineData(8), InlineData(9)
        ]
        public void IsPrime_NonPrimesLessThan10_ReturnFalse(int value) =>
            Assert.False(_primeService.IsPrime(value), $"{value} should not be prime");
    }
}
```

### <a name="create-a-solution"></a>Vytvoření řešení

Z příkazového řádku vytvořte nové řešení pro zapouzdření knihovny tříd a dvou testovacích projektů. Pomocí [`dotnet sln`](../tools/dotnet-sln.md) příkazu:

```dotnetcli
dotnet new sln -n XUnit.Coverage
```

Tím se vytvoří nový název souboru řešení `XUnit.Coverage` v adresáři *UnitTestingCodeCoverage* . Přidejte projekty do kořenového adresáře řešení.

## <a name="linux"></a>[Linux](#tab/linux)

```dotnetcli
dotnet sln XUnit.Coverage.sln add **/*.csproj --in-root
```

## <a name="windows"></a>[Windows](#tab/windows)

```dotnetcli
dotnet sln XUnit.Coverage.sln add (ls **/*.csproj) --in-root
```

---

Sestavte řešení pomocí [`dotnet build`](../tools/dotnet-build.md) příkazu:

```dotnetcli
dotnet build
```

Pokud je sestavení úspěšné, vytvořili jste tři projekty, vhodně odkazované projekty a balíčky a správně aktualizovali zdrojový kód. Hotovo!

## <a name="tooling"></a>Nástroje

Existují dva typy nástrojů pokrytí kódu:

- **Kolekce** DataCollectors: Kolekce DataCollectors monitorují provádění testů a shromažďují informace o testovacích běhůch. Nahlásí shromážděné informace v různých výstupních formátech, jako je XML a JSON. Další informace najdete v tématu [Váš první sběrač](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/datacollector.md).
- **Generátory sestav:** Použijte data shromážděná z testovacích běhů ke generování sestav, často jako ve stylu HTML.

V této části se zaměřujete na nástroje kolekce dat. Aby bylo možné používat Coverlet pro pokrytí kódu, existující projekt testování částí musí mít příslušné závislosti balíčků, nebo případně spoléhat na [globální nástroje .NET](../tools/global-tools.md) a odpovídající balíček NuGet [Coverlet. Console](https://www.nuget.org/packages/coverlet.console) .

## <a name="integrate-with-net-test"></a>Integrace s .NET testem

Šablona projektu testů xUnit se ve výchozím nastavení integruje s [coverlet. collector](https://www.nuget.org/packages/coverlet.collector) .
Z příkazového řádku změňte adresáře na projekt *XUnit. Coverlet. collector* a spusťte [`dotnet test`](../tools/dotnet-test.md) příkaz:

```dotnetcli
cd XUnit.Coverlet.Collector && dotnet test --collect:"XPlat Code Coverage"
```

> [!NOTE]
> `"XPlat Code Coverage"`Argument je popisný název, který odpovídá sběračům dat z Coverlet. Tento název je povinný, ale rozlišuje velká a malá písmena.

V rámci `dotnet test` spuštění je výsledný soubor *coverage.cobertura.xml* výstupem do adresáře *TestResults* . Soubor XML obsahuje výsledky. Jedná se o možnost pro různé platformy, která spoléhá na .NET Core CLI a je ideální pro systémy sestavení, kde nástroj MSBuild není k dispozici.

Níže je příklad souboru *coverage.cobertura.xml* .

```xml
<?xml version="1.0" encoding="utf-8"?>
<coverage line-rate="1" branch-rate="1" version="1.9" timestamp="1592248008"
          lines-covered="12" lines-valid="12" branches-covered="6" branches-valid="6">
  <sources>
    <source>C:\</source>
  </sources>
  <packages>
    <package name="Numbers" line-rate="1" branch-rate="1" complexity="6">
      <classes>
        <class name="Numbers.PrimeService" line-rate="1" branch-rate="1" complexity="6"
               filename="Numbers\PrimeService.cs">
          <methods>
            <method name="IsPrime" signature="(System.Int32)" line-rate="1"
                    branch-rate="1" complexity="6">
              <lines>
                <line number="8" hits="11" branch="False" />
                <line number="9" hits="11" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="7" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="10" hits="3" branch="False" />
                <line number="11" hits="3" branch="False" />
                <line number="14" hits="22" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="57" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="15" hits="7" branch="False" />
                <line number="16" hits="7" branch="True" condition-coverage="100% (2/2)">
                  <conditions>
                    <condition number="27" type="jump" coverage="100%" />
                  </conditions>
                </line>
                <line number="17" hits="4" branch="False" />
                <line number="18" hits="4" branch="False" />
                <line number="20" hits="3" branch="False" />
                <line number="21" hits="4" branch="False" />
                <line number="23" hits="11" branch="False" />
              </lines>
            </method>
          </methods>
          <lines>
            <line number="8" hits="11" branch="False" />
            <line number="9" hits="11" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="7" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="10" hits="3" branch="False" />
            <line number="11" hits="3" branch="False" />
            <line number="14" hits="22" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="57" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="15" hits="7" branch="False" />
            <line number="16" hits="7" branch="True" condition-coverage="100% (2/2)">
              <conditions>
                <condition number="27" type="jump" coverage="100%" />
              </conditions>
            </line>
            <line number="17" hits="4" branch="False" />
            <line number="18" hits="4" branch="False" />
            <line number="20" hits="3" branch="False" />
            <line number="21" hits="4" branch="False" />
            <line number="23" hits="11" branch="False" />
          </lines>
        </class>
      </classes>
    </package>
  </packages>
</coverage>
```

> [!TIP]
> Jako alternativu můžete použít balíček MSBuild, pokud systém sestavení již využívá MSBuild. Z příkazového řádku změňte adresáře na projekt *XUnit. Coverlet. MSBuild* a spusťte `dotnet test` příkaz:
>
> ```dotnetcli
> dotnet test /p:CollectCoverage=true /p:CoverletOutputFormat=cobertura
> ```
>
> Výsledný soubor *coverage.cobertura.xml* je výstup.  
> [Tady](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/MSBuildIntegration.md) můžete postupovat podle příručky integraton MSBuild.

## <a name="generate-reports"></a>Generování sestav

Teď, když máte možnost shromažďovat data z testů jednotek, můžete generovat sestavy pomocí [ReportGenerator](https://github.com/danielpalme/ReportGenerator). Pokud chcete nainstalovat balíček NuGet [ReportGenerator](https://www.nuget.org/packages/dotnet-reportgenerator-globaltool) jako [globální nástroj .NET](../tools/global-tools.md), použijte [`dotnet tool install`](../tools/dotnet-tool-install.md) příkaz:

```dotnetcli
dotnet tool install -g dotnet-reportgenerator-globaltool
```

Spusťte nástroj a poskytněte požadované možnosti podle výstupního *coverage.cobertura.xml* souboru z předchozího testovacího běhu.

```console
reportgenerator
"-reports:Path\To\TestProject\TestResults\{guid}\coverage.cobertura.xml"
"-targetdir:coveragereport"
-reporttypes:Html
```

Po spuštění tohoto příkazu představuje soubor HTML vygenerovanou sestavu.

:::image type="content" source="media/test-report.png" lightbox="media/test-report.png" alt-text="Sestava generovaná testem jednotek":::

## <a name="see-also"></a>Viz také

- [Pokrytí pokrytí testu jednotek sady Visual Studio](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested)
- [Coverlet úložiště GitHubu](https://github.com/coverlet-coverage/coverlet)
- [ReportGenerator úložiště GitHubu](https://github.com/danielpalme/ReportGenerator)
- [Projektový web ReportGenerator](https://danielpalme.github.io/ReportGenerator)
- [Příkaz .NET Core CLI test](../tools/dotnet-test.md)

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Osvědčené postupy pro testování částí](unit-testing-best-practices.md)
