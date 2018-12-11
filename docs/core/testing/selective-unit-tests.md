---
title: Spouštění selektivních testů jednotek
description: Jak pomocí výrazu filtru spouštění selektivních testů jednotek pomocí příkazu dotnet test v .NET Core.
author: smadala
ms.date: 03/22/2017
ms.custom: seodec18
ms.openlocfilehash: 1a90438e3b0b2eb095124208010bbe9558424d91
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170186"
---
# <a name="running-selective-unit-tests"></a>Spouštění selektivních testů jednotek

Následující příklady používají `dotnet test`. Pokud používáte `vstest.console.exe`, nahraďte `--filter ` s `--testcasefilter:`.

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
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Spustí testy, které jsou ve třídě `MSTestNamespace.UnitTest1`.<br>**Poznámka:** `ClassName` Hodnota by měla mít oboru názvů, tak `ClassName=UnitTest1` nebude fungovat. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Spustí všechny testy s výjimkou `MSTestNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Spustí testy, které jsou opatřeny poznámkami s `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Spustí testy, které jsou opatřeny poznámkami s `[Priority(2)]`.<br>

**Použití podmíněných operátorů | a &amp;**

| Výraz | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **nebo** `TestCategory` je `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTest1` **a** `TestCategory` je `CategoryA` **nebo** `Priority` 1. |

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
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Pouze jeden test spouští `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Spustí všechny testy s výjimkou `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Spustí testy, jejichž zobrazované jméno obsahuje `TestClass1`. |

V příkladu kódu, jsou definované vlastnosti s klíči `Category` a `Priority` lze použít pro filtrování.

| Výraz | Výsledek |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Spustí testy, jejichž `FullyQualifiedName` obsahuje `XUnit`.  K dispozici v `vstest 15.1+`. |
| `dotnet test --filter Category=CategoryA` | Spustí testy, které mají `[Trait("Category", "CategoryA")]`. |

**Použití podmíněných operátorů | a &amp;**

| Výraz | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | Spuštění testů, které má `TestClass1` v `FullyQualifiedName` **nebo** `Category` je `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | Spuštění testů, které má `TestClass1` v `FullyQualifiedName` **a** `Category` je `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | Spustí testy, které mají buď `FullyQualifiedName` obsahující `TestClass1` **a** `Category` je `CategoryA` **nebo** `Priority` 1. |

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
| `dotnet test --filter TestCategory=CategoryA` | Spustí testy, které jsou opatřeny poznámkami s `[Category("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Spustí testy, které jsou opatřeny poznámkami s `[Priority(2)]`.<br>

**Použití podmíněných operátorů | a &amp;**

| Výraz | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **nebo** `TestCategory` je `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Spustí testy, které mají `UnitTest1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTest1` **a** `TestCategory` je `CategoryA` **nebo** `Priority` 1. |
