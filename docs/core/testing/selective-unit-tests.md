---
title: Spouštění selektivních testů jednotek
description: Jak použít výraz filtru ke spuštění selektivních testů jednotek pomocí příkazu dotnet test v .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: 57428dad2de6c2507ca2cdc42e3df9e83a1edd69
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715462"
---
# <a name="running-selective-unit-tests"></a>Spouštění selektivních testů jednotek

Pomocí příkazu `dotnet test` v rozhraní .NET Core můžete použít výraz filtru ke spuštění selektivních testů. Tento článek ukazuje, jak filtrovat, který test se spouští. Následující příklady používají `dotnet test`. Pokud používáte `vstest.console.exe`, nahraďte `--filter` `--testcasefilter:`.

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

| Výraz | Výsledek |
| ---------- | ------ |
| `dotnet test --filter Method` | Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`. K dispozici v `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Spustí testy, jejichž název obsahuje `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Spustí testy, které jsou ve třídě `MSTestNamespace.UnitTest1`.<br>**Poznámka:** Hodnota `ClassName` by měla mít obor názvů, takže `ClassName=UnitTest1` nebude fungovat. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Spustí všechny testy s výjimkou `MSTestNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Spustí testy, které jsou poznámy s `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Spustí testy, které jsou poznámy s `[Priority(2)]`.<br>

**Použití podmíněných operátorů | a &amp;**

| Výraz | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **nebo** `TestCategory` `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTest1` **a** `TestCategory` jsou `CategoryA` **nebo** `Priority` 1. |

## <a name="xunit"></a>xUnit

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

| Výraz | Výsledek |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Spustí pouze jeden test, `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Spustí všechny testy s výjimkou `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Spustí testy, jejichž zobrazovaný název obsahuje `TestClass1`. |

V příkladu kódu lze pro filtrování použít definované vlastnosti s klíči `Category` a `Priority`.

| Výraz | Výsledek |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Spustí testy, jejichž `FullyQualifiedName` obsahuje `XUnit`.  K dispozici v `vstest 15.1+`. |
| `dotnet test --filter Category=CategoryA` | Spustí testy, které mají `[Trait("Category", "CategoryA")]`. |

**Použití podmíněných operátorů | a &amp;**

| Výraz | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | Spustí testy, které mají `TestClass1` v `FullyQualifiedName` **nebo** `Category` `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | Spustí testy, které mají `TestClass1` v `FullyQualifiedName` **a** `Category` je `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | Spustí testy, které mají buď `FullyQualifiedName` obsahující `TestClass1` **a** `Category` jsou `CategoryA` **nebo** `Priority` 1. |

## <a name="nunit"></a>NUnit

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

| Výraz | Výsledek |
| ---------- | ------ |
| `dotnet test --filter Method` | Spustí testy, jejichž `FullyQualifiedName` obsahuje `Method`. K dispozici v `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Spustí testy, jejichž název obsahuje `TestMethod1`. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Spustí testy, které jsou ve třídě `NUnitNamespace.UnitTest1`.<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Spustí všechny testy s výjimkou `NUnitNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Spustí testy, které jsou poznámy s `[Category("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Spustí testy, které jsou poznámy s `[Priority(2)]`.<br>

**Použití podmíněných operátorů | a &amp;**

| Výraz | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **nebo** `TestCategory` `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTest1` **a** `TestCategory` jsou `CategoryA` **nebo** `Priority` 1. |
