---
title: Funkce C# podporující LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: af7bf487ff4ed250025b946f0948c269fcc5bf09
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418565"
---
# <a name="c-features-that-support-linq"></a>Funkce C# podporující LINQ

V následující části jsou představeny nové jazykové konstrukce představené v C# 3,0. I když jsou tyto nové funkce využité pro určitý stupeň s [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy, nejsou omezené na [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] a dají se použít v jakémkoli kontextu, kde je najdete užitečné.

## <a name="query-expressions"></a>Výrazy dotazu

Výrazy dotazů používají deklarativní syntaxi podobnou syntaxi SQL nebo XQuery pro dotazování přes kolekce IEnumerable. Syntaxe dotazu v době kompilace je převedena na volání metody do implementace standardních metod rozšíření operátoru dotazu na poskytovatele [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Aplikace řídí standardní operátory dotazů, které jsou v oboru, zadáním příslušného oboru názvů s direktivou `using`. Následující výraz dotazu přebírá pole řetězců, seskupuje je podle prvního znaku v řetězci a řadí skupiny.

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

Proměnné deklarované jako `var` jsou stejně silného typu jako proměnné, jejichž typ zadáte explicitně. Použití `var` umožňuje vytvořit anonymní typy, ale lze je použít pouze pro místní proměnné. Pole lze také deklarovat pomocí implicitního zadání.

Další informace naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).

## <a name="object-and-collection-initializers"></a>Inicializátory objektu a kolekce

Inicializátory objektů a kolekcí umožňují inicializovat objekty bez explicitního volání konstruktoru objektu. Inicializátory se obvykle používají ve výrazech dotazů při projektování zdrojových dat do nového datového typu. Za předpokladu, že třída s názvem `Customer` s vlastnostmi Public `Name` a `Phone`, může být inicializátor objektu použit jako v následujícím kódu:

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

Pokud budete pokračovat s naší `Customer`ou třídou, předpokládáme, že existuje zdroj dat s názvem `IncomingOrders`a že pro každou objednávku s velkým `OrderSize`chtěli bychom vytvořit nový `Customer` založený na tomto pořadí. V tomto zdroji dat lze spustit dotaz LINQ a k vyplnění kolekce použít inicializaci objektu:

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

Zdroj dat může mít více vlastností ležící pod digestoří, než `Customer`á třída, jako je například `OrderSize`, ale při inicializaci objektu se data vrácená z dotazu molded do požadovaného datového typu. Vybíráme data, která jsou relevantní pro naši třídu. Výsledkem je, že teď máme `IEnumerable` vyplněnou novými `Customer`y, které jsme chtěli. Výše uvedený postup lze také zapsat v syntaxi metody LINQ:

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

Další informace naleznete v tématu:

- [Inicializátory objektu a kolekce](../../classes-and-structs/object-and-collection-initializers.md)

- [Syntaxe výrazu dotazu pro standardní operátory dotazu](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>Anonymní typy

Anonymní typ je vytvořen kompilátorem a název typu je k dispozici pouze pro kompilátor. Anonymní typy poskytují pohodlný způsob, jak dočasně seskupit sadu vlastností do výsledku dotazu bez nutnosti definovat samostatný pojmenovaný typ. Anonymní typy jsou inicializovány s novým výrazem a inicializátorem objektu, jak je znázorněno zde:

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

Další informace najdete v tématu [anonymní typy](../../classes-and-structs/anonymous-types.md).

## <a name="extension-methods"></a>Metody rozšíření

Rozšiřující metoda je statická metoda, která může být přidružena k typu, aby mohla být volána jako metoda instance typu. Tato funkce umožňuje přidat nové metody do stávajících typů, aniž by bylo nutné je skutečně upravovat. Standardní operátory dotazu jsou sada rozšiřujících metod, které poskytují [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] funkce dotazů pro jakýkoli typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>.

Další informace naleznete v tématu [metody rozšíření](../../classes-and-structs/extension-methods.md).

## <a name="lambda-expressions"></a>Lambda – výrazy

Výraz lambda je vložená funkce, která používá operátor = > pro oddělení vstupních parametrů z těla funkce a může být převedena v době kompilace na delegáta nebo strom výrazu. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programování dojde při přímé volání metody do standardních operátorů dotazů na lambda výrazy.

Další informace naleznete v tématu:

- [Anonymní funkce](../../statements-expressions-operators/anonymous-functions.md)

- [Výrazy lambda](../../statements-expressions-operators/lambda-expressions.md)

- [Stromy výrazů (C#)](../expression-trees/index.md)

## <a name="see-also"></a>Viz také:

- [Dotaz integrovaný na jazyku (LINQ)C#()](./index.md)
