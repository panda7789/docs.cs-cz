---
title: Spouštění selektivních testů jednotek
description: Použití výrazu filtru ke spuštění selektivních testů částí pomocí příkazu dotnet test v rozhraní .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: b9156300587215e68c01c609e298dbc1a2c53d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543505"
---
# <a name="running-selective-unit-tests"></a>Spouštění selektivních testů jednotek

Pomocí `dotnet test` příkazu v majekně .NET Core můžete ke spuštění selektivních testů použít výraz filtru. Tento článek ukazuje, jak filtrovat, které test jsou spuštěny. Následující příklady `dotnet test`používají . Pokud používáte `vstest.console.exe`, `--filter` nahraďte na `--testcasefilter:`.

> [!NOTE]
> Použití filtrů, které obsahují vykřičník (!) na `*nix` vyžaduje úniku, protože `!` je vyhrazena. Tento filtr například přeskočí všechny testy, pokud `dotnet test --filter FullyQualifiedName\!~IntegrationTests`obor názvů obsahuje IntegrationTests: .
> Všimněte si zpětného lomítka, které předchází vykřičník.

## <a name="mstest"></a>MSTest

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestCategory("CategoryA")]
        [Priority(1)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [Priority(2)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| Expression | Výsledek |
| ---------- | ------ |
| `dotnet test --filter Method` | Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`. K `vstest 15.1+`dispozici v . |
| `dotnet test --filter Name~TestMethod1` | Spustí testy, `TestMethod1`jejichž název obsahuje . |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Spustí testy, které `MSTestNamespace.UnitTest1`jsou ve třídě .<br>**Poznámka:** Hodnota `ClassName` by měla mít obor `ClassName=UnitTest1` názvů, takže nebude fungovat. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Spustí všechny `MSTestNamespace.UnitTest1.TestMethod1`testy s výjimkou . |
| `dotnet test --filter TestCategory=CategoryA` | Spustí testy, které jsou `[TestCategory("CategoryA")]`anotovány s . |
| `dotnet test --filter Priority=2` | Spustí testy, které jsou `[Priority(2)]`anotovány s .<br>

**Použití podmíněných operátorů | A&amp;**

| Expression | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Spustí testy, `UnitTest1` `FullyQualifiedName` které `CategoryA`mají v **nebo** `TestCategory` je . |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Spustí testy, `UnitTest1` `FullyQualifiedName` které `CategoryA`mají v **.** `TestCategory` |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Spustí testy, `FullyQualifiedName` které `UnitTest1` **and** `TestCategory` obsahují `CategoryA` a je **nebo** `Priority` je 1. |

## <a name="xunit"></a>xJednotka

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "CategoryA")]
        [Trait("Priority", "1")]
        [Fact]
        public void Test1()
        {
        }

        [Trait("Priority", "2")]
        [Fact]
        public void Test2()
        {
        }
    }
}
```

| Expression | Výsledek |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Spustí pouze jeden `XUnitNamespace.TestClass1.Test1`test, . |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Spustí všechny `XUnitNamespace.TestClass1.Test1`testy s výjimkou . |
| `dotnet test --filter DisplayName~TestClass1` | Spustí testy, jejichž `TestClass1`zobrazovaný název obsahuje . |

V příkladu kódu definované vlastnosti `Category` `Priority` s klíči a lze použít pro filtrování.

| Expression | Výsledek |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Spustí testy, jejichž `FullyQualifiedName` obsahuje `XUnit`.  K `vstest 15.1+`dispozici v . |
| `dotnet test --filter Category=CategoryA` | Spustí testy, `[Trait("Category", "CategoryA")]`které mají . |

**Použití podmíněných operátorů | A&amp;**

| Expression | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | Spustí testy, `TestClass1` `FullyQualifiedName` které `CategoryA`má v **nebo** `Category` je . |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | Spustí testy, `TestClass1` `FullyQualifiedName` které `CategoryA`má v **a** `Category` je . |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | Spustí testy, `FullyQualifiedName` které `TestClass1` **and** `Category` obsahují `CategoryA` a je **nebo** `Priority` je 1. |

## <a name="nunit"></a>NJednotka

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Category("CategoryA")]
        [Property("Priority", 1)]
        [Test]
        public void TestMethod1()
        {
        }

        [Property("Priority", 2)]
        [Test]
        public void TestMethod2()
        {
        }
    }
}
```

| Expression | Výsledek |
| ---------- | ------ |
| `dotnet test --filter Method` | Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`. K `vstest 15.1+`dispozici v . |
| `dotnet test --filter Name~TestMethod1` | Spustí testy, `TestMethod1`jejichž název obsahuje . |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Spustí testy, které `NUnitNamespace.UnitTest1`jsou ve třídě .<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Spustí všechny `NUnitNamespace.UnitTest1.TestMethod1`testy s výjimkou . |
| `dotnet test --filter TestCategory=CategoryA` | Spustí testy, které jsou `[Category("CategoryA")]`anotovány s . |
| `dotnet test --filter Priority=2` | Spustí testy, které jsou `[Priority(2)]`anotovány s .<br>

**Použití podmíněných operátorů | A&amp;**

| Expression | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Spustí testy, `UnitTest1` `FullyQualifiedName` které `CategoryA`mají v **nebo** `TestCategory` je . |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Spustí testy, `UnitTest1` `FullyQualifiedName` které `CategoryA`mají v **.** `TestCategory` |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Spustí testy, `FullyQualifiedName` které `UnitTest1` **and** `TestCategory` obsahují `CategoryA` a je **nebo** `Priority` je 1. |
