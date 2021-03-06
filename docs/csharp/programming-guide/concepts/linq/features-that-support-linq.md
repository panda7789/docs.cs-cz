---
title: Funkce C# podporující LINQ
description: Přečtěte si o funkcích jazyka C# pro použití s dotazy LINQ a v jiných kontextech. Tyto jazykové konstrukce byly představeny v C# 3,0.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 13254c69193e04ffcf11e3e23f1deb460063a6c1
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063689"
---
# <a name="c-features-that-support-linq"></a>Funkce C# podporující LINQ

V následující části jsou představeny nové jazykové konstrukce představené v C# 3,0. I když jsou tyto nové funkce použity ve stupních s dotazy LINQ, nejsou omezeny na LINQ a je možné je použít v jakémkoli kontextu, kde je najdete užitečné.

## <a name="query-expressions"></a>Výrazy dotazu

Výrazy dotazů používají deklarativní syntaxi podobnou syntaxi SQL nebo XQuery pro dotazování přes kolekce IEnumerable. Syntaxe dotazu v čase kompilace je převedena na volání metody do implementace metod rozšíření standardních operátorů dotazu poskytovatele LINQ. Aplikace řídí standardní operátory dotazů, které jsou v oboru, zadáním příslušného oboru názvů s `using` direktivou. Následující výraz dotazu přebírá pole řetězců, seskupuje je podle prvního znaku v řetězci a řadí skupiny.

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

Další informace najdete v tématu [výrazy dotazů LINQ](../../../linq/index.md).

## <a name="implicitly-typed-variables-var"></a>Implicitně typované proměnné (var)

Namísto explicitního určení typu při deklaraci a inicializaci proměnné lze použít modifikátor [var](../../../language-reference/keywords/var.md) k tomu, aby kompilátor mohl odvodit a přiřadit typ, jak je znázorněno zde:

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

Proměnné deklarované jako `var` jsou pouze silně typované jako proměnné, jejichž typ zadáte explicitně. Použití je `var` možné vytvořit anonymní typy, ale lze je použít pouze pro místní proměnné. Pole lze také deklarovat pomocí implicitního zadání.

Další informace naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).

## <a name="object-and-collection-initializers"></a>Inicializátory objektu a kolekce

Inicializátory objektů a kolekcí umožňují inicializovat objekty bez explicitního volání konstruktoru objektu. Inicializátory se obvykle používají ve výrazech dotazů při projektování zdrojových dat do nového datového typu. Za předpokladu, že třída s názvem `Customer` Public `Name` a `Phone` Properties, může být inicializátor objektu použit jako v následujícím kódu:

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

V případě pokračování v naší `Customer` třídě se předpokládá, že je k dispozici zdroj dat `IncomingOrders` s názvem a že pro každou objednávku má velký `OrderSize` , chtěli bychom vytvořit nové `Customer` založené na tomto pořadí. V tomto zdroji dat lze spustit dotaz LINQ a k vyplnění kolekce použít inicializaci objektu:

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

Zdroj dat může mít více vlastností ležící pod digestoří, než je `Customer` třída, jako `OrderSize` je například, ale s inicializací objektu, data vrácená z dotazu jsou molded na požadovaný datový typ. vybíráme data, která jsou relevantní pro naši třídu. V důsledku toho jsme teď `IEnumerable` naplnili nové s, které `Customer` jsme chtěli. Výše uvedený postup lze také zapsat v syntaxi metody LINQ:

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

Další informace:

- [Inicializátory objektu a kolekce](../../classes-and-structs/object-and-collection-initializers.md)

- [Syntaxe výrazu dotazu pro standardní operátory dotazu](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>Anonymní typy

Anonymní typ je vytvořen kompilátorem a název typu je k dispozici pouze pro kompilátor. Anonymní typy poskytují pohodlný způsob, jak dočasně seskupit sadu vlastností do výsledku dotazu bez nutnosti definovat samostatný pojmenovaný typ. Anonymní typy jsou inicializovány s novým výrazem a inicializátorem objektu, jak je znázorněno zde:

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

Další informace najdete v tématu [anonymní typy](../../classes-and-structs/anonymous-types.md).

## <a name="extension-methods"></a>Metody rozšíření

Rozšiřující metoda je statická metoda, která může být přidružena k typu, aby mohla být volána jako metoda instance typu. Tato funkce umožňuje přidat nové metody do stávajících typů, aniž by bylo nutné je skutečně upravovat. Standardní operátory dotazu jsou sada rozšiřujících metod, které poskytují funkce dotazů LINQ pro jakýkoli typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> .

Další informace naleznete v tématu [metody rozšíření](../../classes-and-structs/extension-methods.md).

## <a name="lambda-expressions"></a>Lambda – výrazy

Výraz lambda je vložená funkce, která používá operátor => pro oddělení vstupních parametrů z těla funkce a může být převedena v době kompilace na delegáta nebo strom výrazu. V programování LINQ dojde k vyvolání výrazů lambda při přímém volání metody do standardních operátorů dotazu.

Další informace:

- [Anonymní funkce](../../statements-expressions-operators/anonymous-functions.md)

- [Výrazy lambda](../../../language-reference/operators/lambda-expressions.md)

- [Stromy výrazů (C#)](../expression-trees/index.md)

## <a name="see-also"></a>Viz také

- [LINQ (Language-Integrated Query) (C#)](./index.md)
