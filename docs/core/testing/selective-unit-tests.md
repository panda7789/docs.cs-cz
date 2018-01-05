---
title: "Testy spuštění selektivní jednotek"
description: "Ukazuje, jak se použije ke spuštění testů jednotek selektivní test příkazem dotnet výraz filtru."
keywords: "Testování částí rozhraní .NET, .NET core, selektivní testu"
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13d01272-bbf8-456c-a97a-560001d1a7f2
ms.workload: dotnetcore
ms.openlocfilehash: a650e971afd63171b0cc12f679d81bc222a609a5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="running-selective-unit-tests"></a>Testy spuštění selektivní jednotek

Následující příklady použití `dotnet test`. Pokud používáte `vstest.console.exe`, nahraďte `--filter ` s `--testcasefilter:`.

## <a name="mstest"></a>MSTest

```csharp
namespace MSTestNamespace
{
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    [TestClass]
    public class UnitTestClass1
    {
        [Priority(2)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [TestCategory("CategoryA")]
        [Priority(3)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| Výraz | Výsledek |
| ---------- | ------ |
| `dotnet test --filter Method` | Spuštění testů, jehož `FullyQualifiedName` obsahuje `Method`. K dispozici v `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Spustí testy, jejichž název obsahuje `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | Spustí testy, které jsou ve třídě `MSTestNamespace.UnitTestClass1`.<br>**Poznámka:** `ClassName` hodnota musí mít obor názvů, takže `ClassName=UnitTestClass1` nebude fungovat. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | Spustí všechny testy kromě `MSTestNamespace.UnitTestClass1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Spustí testy, které jsou opatřen poznámkou `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=3` | Spustí testy, které jsou opatřen poznámkou `[Priority(3)]`.<br>**Poznámka:** `Priority~3` je neplatná hodnota, protože není řetězec. |

**Podmíněné operátory pomocí | a&amp;**

| Výraz | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | Spustí testy, které mají `UnitTestClass1` v `FullyQualifiedName` **nebo** `TestCategory` je `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | Spustí testy, které mají `UnitTestClass1` v `FullyQualifiedName` **a** `TestCategory` je `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | Spustí testy, které mají buď `FullyQualifiedName` obsahující `UnitTestClass1` **a** `TestCategory` je `CategoryA` **nebo** `Priority` je 1. |

## <a name="xunit"></a>xUnit

```csharp
namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "bvt")]
        [Trait("Priority", "1")]
        [Fact]
        public void foo()
        {
        }

        [Trait("Category", "Nightly")]
        [Trait("Priority", "2")]
        [Fact]
        public void bar()
        {
        }
    }
}
```

| Výraz | Výsledek |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Spouští pouze jeden test `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Spustí všechny testy kromě `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Spustí testy, jejichž název zobrazení obsahuje `TestClass1`. |

V příkladu kódu, jsou definované vlastnosti s klíči `Category` a `Priority` lze použít pro filtrování.

| Výraz | Výsledek |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Spuštění testů, jehož `FullyQualifiedName` obsahuje `XUnit`.  K dispozici v `vstest 15.1+`. |
| `dotnet test --filter Category=bvt` | Spustí testy, které mají `[Trait("Category", "bvt")]`. |

**Podmíněné operátory pomocí | a&amp;**

| Výraz | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | Spustí testy, které má `TestClass1` v `FullyQualifiedName` **nebo** `Category` je `Nightly`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | Spustí testy, které má `TestClass1` v `FullyQualifiedName` **a** `Category` je `Nightly`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | Spustí testy, které mají buď `FullyQualifiedName` obsahující `TestClass1` **a** `Category` je `CategoryA` **nebo** `Priority` je 1. |
