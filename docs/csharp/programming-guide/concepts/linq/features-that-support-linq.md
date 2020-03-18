---
title: Funkce C# podporující LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 9fc8adaa49d02f8b69c2db6e94a28b9fab36b3b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635792"
---
# <a name="c-features-that-support-linq"></a>Funkce C# podporující LINQ

V následující části zavádí nové jazykové konstrukce zavedené v jazyce C# 3.0. Přestože tyto nové funkce jsou všechny používány do určité míry s dotazy LINQ, nejsou omezeny na LINQ a lze je použít v jakémkoli kontextu, kde je považujete za užitečné.

## <a name="query-expressions"></a>Výrazy dotazu

Výrazy dotazu používají k dotazování přes kolekce IEnumerable deklarativní syntaxi podobné sql nebo xquery. V době kompilace je syntaxe dotazu převedena na volání metody na implementaci standardních metod rozšíření operátoru dotazu poskytovatele LINQ. Aplikace řídí standardní operátory dotazů, které jsou v `using` oboru zadáním příslušného oboru názvů pomocí směrnice. Následující výraz dotazu přebírá pole řetězců, seskupuje je podle prvního znaku v řetězci a uskutečňuje skupiny.

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

Další informace naleznete v tématu [LINQ Query Expressions](../../../linq/index.md).

## <a name="implicitly-typed-variables-var"></a>Implicitně zadané proměnné (var)

Namísto explicitního zadání typu při deklarování a inicializaci proměnné můžete pomocí modifikátoru [var](../../../language-reference/keywords/var.md) instruovat kompilátor, aby odvodil a přiřazoval typ, jak je znázorněno zde:

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

Proměnné deklarované jako `var` jsou stejně silně zadali jako proměnné, jejichž typ zadáte explicitně. Použití `var` umožňuje vytvářet anonymní typy, ale lze jej použít pouze pro místní proměnné. Pole lze také deklarovat s implicitním psaním.

Další informace naleznete [v tématu Implicitně zadané místní proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).

## <a name="object-and-collection-initializers"></a>Inicializátory objektu a kolekce

Inicializátory objektu a kolekce umožňují inicializovat objekty bez explicitního volání konstruktoru pro objekt. Inicializátory se obvykle používají ve výrazech dotazu při promítat zdrojová data do nového datového typu. Za předpokladu, `Name` že `Phone` třída s názvem `Customer` public a vlastnosti, inicializátor objektu lze použít jako v následujícím kódu:

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

Pokračování s `Customer` naší třídy, předpokládejme, `IncomingOrders`že je zdroj dat s `OrderSize`názvem , a že `Customer` pro každou objednávku s velkým , bychom chtěli vytvořit nový na základě mimo tuto objednávku. Dotaz LINQ lze spustit na tomto zdroji dat a použít inicializaci objektu k vyplnění kolekce:

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

Zdroj dat může mít více vlastností `Customer` ležících `OrderSize`pod kapotou než třída, například , ale s inicializací objektu jsou data vrácená z dotazu vylisována do požadovaného datového typu; vybíráme data, která jsou relevantní pro naši třídu. V důsledku toho máme `IEnumerable` nyní plné `Customer`nových s jsme chtěli. Výše uvedené lze také zapsat do syntaxe metody LINQ:

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

Další informace naleznete v tématu:

- [Inicializátory objektu a kolekce](../../classes-and-structs/object-and-collection-initializers.md)

- [Syntaxe výrazu dotazu pro standardní operátory dotazu](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>Anonymní typy

Anonymní typ je vytvořen kompilátorem a název typu je k dispozici pouze kompilátoru. Anonymní typy poskytují pohodlný způsob, jak dočasně seskupit sadu vlastností ve výsledku dotazu bez nutnosti definovat samostatný pojmenovaný typ. Anonymní typy jsou inicializovány s novým výrazem a inicializátorem objektu, jak je znázorněno zde:

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

Další informace naleznete [v tématu Anonymní typy](../../classes-and-structs/anonymous-types.md).

## <a name="extension-methods"></a>Metody rozšíření

Metoda rozšíření je statická metoda, která může být přidružena k typu, takže ji lze volat, jako by se jednalo o metodu instance u typu. Tato funkce umožňuje, ve skutečnosti "přidat" nové metody stávajících typů bez jejich skutečné úpravy. Standardní operátory dotazu jsou sada rozšiřujících metod, které poskytují funkce <xref:System.Collections.Generic.IEnumerable%601>dotazu LINQ pro libovolný typ, který implementuje .

Další informace naleznete v [tématu Metody rozšíření](../../classes-and-structs/extension-methods.md).

## <a name="lambda-expressions"></a>Lambda – výrazy

Výraz lambda je vložená funkce, která používá operátor => k oddělení vstupních parametrů z těla funkce a lze jej v době kompilace převést na delegáta nebo strom výrazů. V programování LINQ se setkáte s výrazy lambda při volání přímé metody pro operátory standardnídotaz.

Další informace naleznete v tématu:

- [Anonymní funkce](../../statements-expressions-operators/anonymous-functions.md)

- [Lambda výrazy](../../statements-expressions-operators/lambda-expressions.md)

- [Stromy výrazů (C#)](../expression-trees/index.md)

## <a name="see-also"></a>Viz také

- [Dotaz integrovaný jazykem (LINQ) (C#)](./index.md)
