---
title: operátor new - C# odkaz
ms.custom: seodec18
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 1c14d50e31b89f4c77c94e5899e8207766a3540f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661149"
---
# <a name="new-operator-c-reference"></a>New – operátor (referenční dokumentace jazyka C#)

Použít k vytvoření objektů a vyvolávání konstruktorů. Příklad:

```csharp
Class1 obj  = new Class1();
```

Používá se také k vytváření instancí anonymních typů:

```csharp
var query = from cust in customers
            select new { Name = cust.Name, Address = cust.PrimaryAddress };
```

`new` Operátor se používá také k vyvolání konstruktoru bez parametrů pro typy hodnot. Příklad:

```csharp
int i = new int();
```

V předchozím příkazu `i` je inicializován na `0`, což je výchozí hodnota pro typ `int`. Příkaz má stejný účinek jako následující:

```csharp
int i = 0;
```

Úplný seznam výchozích hodnot, naleznete v tématu [tabulka výchozích hodnot](default-values-table.md).

Mějte na paměti, že se jedná o chybu deklarovat konstruktor bez parametrů pro [struktura](struct.md) vzhledem k tomu, že každý typ hodnoty má implicitně veřejný konstruktor bez parametrů. Je možné deklarovat konstruktor s parametry u typu Struktura nastavit jeho počáteční hodnoty, ale to je potřeba, pouze pokud jsou požadované hodnoty jiné než výchozí.

Objekty typu hodnoty, jako jsou struktury a objekty typu odkazu, jako jsou třídy, jsou zničeny automaticky, ale objekty typu hodnoty je zničen při zničení jejich obsahující kontext, zatímco objekty typu odkazu jsou zničeny podle uvolňování paměti kolekce neurčené době po odebrání poslední odkazy na ně. Pro typy, které obsahují prostředky, jako jsou popisovače souborů nebo připojení k síti je třeba využívat deterministické vyčištění zajistit, že se prostředky, které obsahují vydávají co nejdříve. Další informace najdete v tématu [příkaz using](using-statement.md).

`new` Operátor nelze přetížit.

Pokud `new` operátor selže přidělování paměti, vyvolá výjimku, <xref:System.OutOfMemoryException>.

## <a name="example"></a>Příklad

V následujícím příkladu `struct` jsou vytvořeny a inicializovány pomocí objektů a objekt třídy `new` operátor a potom přiřadit hodnoty. Zobrazí se výchozí nastavení a přiřazené hodnoty.

[!code-csharp[csrefKeywordsOperator#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#7)]

Všimněte si, že v příkladu, který je výchozí hodnota řetězce `null`. Proto se nezobrazí.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Klíčová slova operátorů](operator-keywords.md)
- [new](new.md)
- [Anonymní typy](../../programming-guide/classes-and-structs/anonymous-types.md)