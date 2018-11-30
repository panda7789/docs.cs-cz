---
title: string (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
ms.openlocfilehash: 66b1729363878f69f868b8b8fd6e9e7011426f27
ms.sourcegitcommit: 7f7664837d35320a0bad3f7e4ecd68d6624633b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2018
ms.locfileid: "52672001"
---
# <a name="string-c-reference"></a>string (Referenční dokumentace jazyka C#)

`string` Typ představuje posloupnost nula nebo více znaků Unicode. `string` je alias pro <xref:System.String> v rozhraní .NET.

I když `string` je typem odkazu, operátory rovnosti (`==` a `!=`) jsou definovány pro porovnání hodnoty `string` objekty, ne odkazuje. Tím je testování rovnosti řetězců intuitivnější. Příklad:

```csharp
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine((object)a == (object)b);
```

Zobrazí "hodnotu True" a potom "False" protože obsah řetězce jsou ekvivalentní, ale `a` a `b` neodkazují na stejné instanci řetězce.

+ – Operátor zřetězí řetězce:

```csharp
string a = "good " + "morning";
```

Tím se vytvoří objekt string obsahující "good morning".

Řetězce jsou *neměnné*– obsah řetězce objektu nelze změnit po vytvoření objektu, přestože je syntaxe zobrazí jako by tomu. Při psaní tohoto kódu kompilátor ve skutečnosti vytváří nový objekt řetězce pro uchování nového pořadí znaků a tento nový objekt je přiřazen b. Řetězec "h" je pak nárok uvolňování paměti.

```csharp
string b = "h";
b += "ello";
```

[] – Operátor slouží pro přístup jen pro čtení k jednotlivé znaky `string`:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Řetězcové literály jsou typu `string` a může být zapsaný ve dvou formách, v uvozovkách a @-quoted. Citovaný řetězec, který literály jsou uzavřeny v dvojitých uvozovkách ("):

```csharp
"good morning"  // a string literal
```

Řetězcové literály může obsahovat libovolný znak literálu. Řídicí sekvence jsou zahrnuty. Následující příklad používá řídicí sekvence `\\` pro zpětné lomítko, `\u0066` písmenem f, a `\n` pro nový řádek.

```csharp
string a = "\\\u0066\n";
Console.WriteLine(a);
```

> [!NOTE]
> Řídicí kód `\udddd` (kde `dddd` je čtyřmístné číslo) představuje znak Unicode U +`dddd`. Osm číslice sady Unicode řídícími kódy jsou také rozpoznána: `\Udddddddd`.

Literály doslovný řetězec začínat `@` a jsou také uzavřen do dvojitých uvozovek. Příklad:

```csharp
@"good morning"  // a string literal
```

Výhodou doslovném řetězci je, že řídicí sekvence jsou *není* zpracování, což usnadňuje zapsat, například plně kvalifikovaný název:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Zahrnout dvojitých uvozovek na @-quoted řetězec, uveďte ji dvakrát:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

Pro další použití `@` speciální znak, naleznete v tématu [@ – Doslovný identifikátor](../tokens/verbatim.md).

Další informace o řetězcích v jazyce C# najdete v tématu [řetězce](../../programming-guide/strings/index.md).

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#17)]  

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Doporučené postupy pro používání řetězců](../../../standard/base-types/best-practices-strings.md)
- [Klíčová slova jazyka C#](index.md)
- [Odkazové typy](reference-types.md)
- [Typy hodnot](value-types.md)
- [Základní operace s řetězci](../../../standard/base-types/basic-string-operations.md)
- [Vytváření nových řetězců](../../../standard/base-types/creating-new.md)
- [Tabulka formátování číselných výsledků](formatting-numeric-results-table.md)
