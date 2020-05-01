---
title: Spouštění selektivních testů jednotek
description: Jak použít výraz filtru ke spuštění selektivních testů jednotek pomocí příkazu dotnet test v .NET Core.
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: e66455b5ac012114c45d998fae11da7ee769fbe2
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624914"
---
# <a name="running-selective-unit-tests"></a>Spouštění selektivních testů jednotek

Pomocí `dotnet test` příkazu v .NET Core můžete použít výraz filtru ke spuštění selektivních testů. Tento článek ukazuje, jak filtrovat, který test se spouští. Následující příklady používají `dotnet test`. Pokud používáte `vstest.console.exe`, nahraďte parametr `--filter` `--testcasefilter:`.

## <a name="character-escaping"></a>Znakové uvozovací znaky

Použití filtrů, které zahrnují vykřičník (!) v `*nix` vyžaduje, aby `!` bylo vyhradit Uvozovací znak. Například tento filtr přeskočí všechny testy, pokud obor názvů obsahuje IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.
Všimněte si zpětného lomítka před vykřičníkem.

Pro `FullyQualifiedName` hodnoty, které obsahují čárku pro parametry obecného typu, oddělte čárku znakem `%2C`. Příklad:

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

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
| `dotnet test --filter Method` | Spustí testy, `FullyQualifiedName` jejichž `Method`obsahuje. K dispozici v `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Spustí testy, jejichž název `TestMethod1`obsahuje. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Spustí testy, které jsou ve `MSTestNamespace.UnitTest1`třídě.<br>**Poznámka:** `ClassName` Hodnota by měla mít obor názvů, takže `ClassName=UnitTest1` nebude fungovat. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Spustí všechny testy s `MSTestNamespace.UnitTest1.TestMethod1`výjimkou. |
| `dotnet test --filter TestCategory=CategoryA` | Spustí testy, které jsou opatřeny `[TestCategory("CategoryA")]`poznámkami. |
| `dotnet test --filter Priority=2` | Spustí testy, které jsou opatřeny `[Priority(2)]`poznámkami.<br>

**Použití podmíněných operátorů | ani&amp;**

| Expression | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Spustí testy, které `UnitTest1` jsou `FullyQualifiedName` v **nebo** `TestCategory` `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Spustí testy, které `UnitTest1` mají `FullyQualifiedName` v **a** `TestCategory` `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | `FullyQualifiedName` Spustí testy, které obsahují `UnitTest1` **a** `TestCategory` jsou `CategoryA` **nebo** `Priority` 1. |

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

| Expression | Výsledek |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Spustí pouze jeden test, `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Spustí všechny testy s `XUnitNamespace.TestClass1.Test1`výjimkou. |
| `dotnet test --filter DisplayName~TestClass1` | Spustí testy, jejichž zobrazovaný název `TestClass1`obsahuje. |

V příkladu kódu jsou definované vlastnosti s klíči `Category` a `Priority` lze je použít pro filtrování.

| Expression | Výsledek |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Spustí testy, `FullyQualifiedName` jejichž `XUnit`obsahuje.  K dispozici v `vstest 15.1+`. |
| `dotnet test --filter Category=CategoryA` | Spustí testy, které `[Trait("Category", "CategoryA")]`mají. |

**Použití podmíněných operátorů | ani&amp;**

| Expression | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | Spustí testy, které `TestClass1` jsou `FullyQualifiedName` v **nebo** `Category` `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | Spustí testy, které `TestClass1` jsou `FullyQualifiedName` v **a** `Category` `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | `FullyQualifiedName` Spustí testy, které obsahují `TestClass1` **a** `Category` jsou `CategoryA` **nebo** `Priority` 1. |

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

| Expression | Výsledek |
| ---------- | ------ |
| `dotnet test --filter Method` | Spustí testy, `FullyQualifiedName` jejichž `Method`obsahuje. K dispozici v `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Spustí testy, jejichž název `TestMethod1`obsahuje. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Spustí testy, které jsou ve `NUnitNamespace.UnitTest1`třídě.<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Spustí všechny testy s `NUnitNamespace.UnitTest1.TestMethod1`výjimkou. |
| `dotnet test --filter TestCategory=CategoryA` | Spustí testy, které jsou opatřeny `[Category("CategoryA")]`poznámkami. |
| `dotnet test --filter Priority=2` | Spustí testy, které jsou opatřeny `[Priority(2)]`poznámkami.<br>

**Použití podmíněných operátorů | ani&amp;**

| Expression | Výsledek |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Spustí testy, které `UnitTest1` jsou `FullyQualifiedName` v **nebo** `TestCategory` `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Spustí testy, které `UnitTest1` mají `FullyQualifiedName` v **a** `TestCategory` `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | `FullyQualifiedName` Spustí testy, které obsahují `UnitTest1` **a** `TestCategory` jsou `CategoryA` **nebo** `Priority` 1. |

Další informace najdete v tématu [testovací případ Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).
