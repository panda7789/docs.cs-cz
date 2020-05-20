---
title: Spouštění selektivních testů jednotek
description: Jak použít výraz filtru ke spuštění selektivních testů jednotek pomocí příkazu dotnet test v .NET Core.
author: smadala
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: 6a6bbb0687742d1e3288d64fb88f6825dc678e28
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702991"
---
# <a name="run-selective-unit-tests"></a>Spouštění selektivních testů jednotek

Pomocí [`dotnet test`](../tools/dotnet-test.md) příkazu v .NET Core můžete použít výraz filtru ke spuštění selektivních testů. Tento článek ukazuje, jak filtrovat, které testy jsou spuštěny. Následující příklady používají `dotnet test` . Pokud používáte `vstest.console.exe` , nahraďte parametr `--filter` `--testcasefilter:` .

## <a name="character-escaping"></a>Znakové uvozovací znaky

Použití filtrů, které zahrnují vykřičník `!` on, `*nix` vyžaduje Uvozovací znak, protože `!` je vyhrazený. Například tento filtr přeskočí všechny testy, pokud obor názvů obsahuje IntegrationTests:

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> Zpětné lomítko předchází vykřičníku, která označuje, že se jedná o řídicí znak `\!` .

Pro `FullyQualifiedName` hodnoty, které obsahují čárku pro parametry obecného typu, oddělte čárku znakem `%2C` . Například:

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

:::zone pivot="mstest"

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod, Priority(1), TestCategory("CategoryA")]
        public void TestMethod1()
        {
        }

        [TestMethod, Priority(2)]
        public void TestMethod2()
        {
        }
    }
}
```

| Výraz | Výsledek |
|--|--|
| `dotnet test --filter Method` | Spustí testy <xref:System.Reflection.Module.FullyQualifiedName> , jejichž obsahuje `Method` . K dispozici v `vstest 15.1+` . |
| `dotnet test --filter Name~TestMethod1` | Spustí testy, jejichž název obsahuje `TestMethod1` . |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Spustí testy, které jsou ve třídě `MSTestNamespace.UnitTest1` .<br>**Poznámka:** `ClassName`Hodnota by měla mít obor názvů, takže `ClassName=UnitTest1` nebude fungovat. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Spustí všechny testy s výjimkou `MSTestNamespace.UnitTest1.TestMethod1` . |
| `dotnet test --filter TestCategory=CategoryA` | Spustí testy, které jsou opatřeny poznámkami `[TestCategory("CategoryA")]` . |
| `dotnet test --filter Priority=2` | Spustí testy, které jsou opatřeny poznámkami `[Priority(2)]` . |

Příklady použití podmíněných operátorů `|` a `&` :

Ke spuštění testů, které mají `UnitTest1` v <xref:System.Reflection.Module.FullyQualifiedName> **nebo** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> jsou `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

Chcete-li spustit testy, které mají `UnitTest1` své <xref:System.Reflection.Module.FullyQualifiedName> **a** mají <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

Pro spuštění testů, které obsahují <xref:System.Reflection.Module.FullyQualifiedName> `UnitTest1` **a** mají <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` **nebo** mají <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> prioritu `1` .

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="xunit"

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Fact, Trait("Priority", "1"), Trait("Category", "CategoryA")]
        public void Test1()
        {
        }

        [Fact, Trait("Priority", "2")]
        public void Test2()
        {
        }
    }
}
```

| Výraz | Výsledek |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Spustí pouze jeden test, `XUnitNamespace.TestClass1.Test1` . |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Spustí všechny testy s výjimkou `XUnitNamespace.TestClass1.Test1` . |
| `dotnet test --filter DisplayName~TestClass1` | Spustí testy, jejichž zobrazovaný název obsahuje `TestClass1` . |

V příkladu kódu jsou definované vlastnosti s klíči `"Category"` a `"Priority"` lze je použít pro filtrování.

| Výraz | Výsledek |
|--|--|
| `dotnet test --filter XUnit` | Spustí testy <xref:System.Reflection.Module.FullyQualifiedName> , jejichž obsahuje `XUnit` .  K dispozici v `vstest 15.1+` . |
| `dotnet test --filter Category=CategoryA` | Spustí testy, které mají `[Trait("Category", "CategoryA")]` . |

Příklady použití podmíněných operátorů `|` a `&` :

Chcete-li spustit testy, které mají `TestClass1` <xref:System.Reflection.Module.FullyQualifiedName> **nebo** mají `Trait` klíč `"Category"` a hodnotu `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

Chcete-li spustit testy, které mají `TestClass1` své <xref:System.Reflection.Module.FullyQualifiedName> **a** mají `Trait` klíč `"Category"` a hodnotu `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

Chcete-li spustit testy, které <xref:System.Reflection.Module.FullyQualifiedName> obsahují `TestClass1` **a** mají `Trait` klíč `"Category"` a hodnotu, `"CategoryA"` **nebo** musí mít `Trait` klíč `"Priority"` a hodnotu `1` .

```dotnetcli
dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="nunit"

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Test, Property("Priority", 1), Category("CategoryA")]
        public void TestMethod1()
        {
        }

        [Test, Property("Priority", 2)]
        public void TestMethod2()
        {
        }
    }
}
```

| Výraz | Výsledek |
|--|--|
| `dotnet test --filter Method` | Spustí testy <xref:System.Reflection.Module.FullyQualifiedName> , jejichž obsahuje `Method` . K dispozici v `vstest 15.1+` . |
| `dotnet test --filter Name~TestMethod1` | Spustí testy, jejichž název obsahuje `TestMethod1` . |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Spustí testy, které jsou ve třídě `NUnitNamespace.UnitTest1` . |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Spustí všechny testy s výjimkou `NUnitNamespace.UnitTest1.TestMethod1` . |
| `dotnet test --filter TestCategory=CategoryA` | Spustí testy, které jsou opatřeny poznámkami `[Category("CategoryA")]` . |
| `dotnet test --filter Priority=2` | Spustí testy, které jsou opatřeny poznámkami `[Priority(2)]` . |

Příklady použití podmíněných operátorů `|` a `&` :

Chcete-li spustit testy, které mají `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **nebo** mají `Category` `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

Chcete-li spustit testy, které mají `UnitTest1` své <xref:System.Reflection.Module.FullyQualifiedName> **a** mají `Category` `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

Chcete-li spustit testy, které mají, <xref:System.Reflection.Module.FullyQualifiedName> obsahující `UnitTest1` **a** mají `Category` nebo, `"CategoryA"` **nebo** musí mít a `Property` `"Priority"` `1` .

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

Další informace najdete v tématu [testovací případ Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

:::zone-end

## <a name="see-also"></a>Viz také

- [dotnet test](../tools/dotnet-test.md)
- [dotnet – test – filtr](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Pořadí testů jednotek](order-unit-tests.md)
