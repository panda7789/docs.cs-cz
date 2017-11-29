---
title: "string (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 87df2b158b173072aad5257594e1b1482ae61067
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="string-c-reference"></a>string (Referenční dokumentace jazyka C#)
`string` Typ reprezentuje posloupnosti nula nebo více znaků Unicode. `string`je alias <xref:System.String> v rozhraní .NET Framework.  
  
 I když `string` typem je odkaz, operátory rovnosti (`==` a `!=`) jsou definovány pro porovnání hodnot `string` objekty, není odkazuje. Díky tomu bude testování rovnosti řetězec intuitivnější. Příklad:  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 Zobrazí "hodnotu True" a potom "False" vzhledem k tomu, že obsah řetězce jsou ekvivalentní, ale `a` a `b` neměly by konce odkazovat na stejnou instanci řetězec.  
  
 + – Operátor zřetězí řetězec:  
  
```csharp  
string a = "good " + "morning";  
```  
  
 Tím se vytvoří objekt řetězec, který obsahuje "Dobré ráno".  
  
 Řetězce jsou *neměnné*– obsah objektu řetězce nelze změnit po vytvoření objektu, i když je syntaxe se objevit, jako kdyby to provedete. Když píšete tento kód, kompilátor ve skutečnosti vytvoří nový objekt řetězec k uložení nové pořadí znaků a tento nový objekt je přiřazen k b. Řetězec "h" je pak vhodné pro uvolňování paměti.  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 [] – Operátor lze použít pro přístup jen pro čtení k jednotlivé znaky `string`:  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 Textové literály jsou typu `string` a může být napsán ve dvou formách, v uvozovkách a @-quoted. V uvozovkách řetězec, který literály jsou uzavřené v uvozovkách ("):  
  
```csharp  
"good morning"  // a string literal  
```  
  
 Textové literály může obsahovat libovolný znak literálu. Řídicí sekvence jsou zahrnuty. Následující příklad používá řídicí sekvence `\\` pro zpětné lomítko, `\u0066` pro písmenem f, a `\n` pro nový řádek.  
  
```  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  Řídicí kód `\udddd` (kde `dddd` čtyři číslice) představuje znak Unicode U +`dddd`. Kódy řídicí Unicode číslice osm jsou také rozpoznána: `\Udddddddd`.  
  
 Typu verbatim textové literály začínat a jsou také uzavřena v uvozovkách. Příklad:  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 Výhodou typu verbatim řetězce je, že jsou řídicí sekvence *není* zpracovat, což usnadňuje zápisu, například plně kvalifikovaný název souboru:  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 Zahrnout uvozovky v @-quoted řetězce, dvakrát ho:  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 Použití jiné @ symbol používat odkazuje ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) identifikátory, které jsou klíčová slova jazyka C#.  
  
 Další informace o řetězcích v jazyce C# najdete v tématu [řetězce](../../../csharp/programming-guide/strings/index.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Osvědčené postupy pro používání řetězců](../../../standard/base-types/best-practices-strings.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
 [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
 [Základní operace s řetězci](../../../standard/base-types/basic-string-operations.md)  
 [Vytváření nových řetězců](../../../standard/base-types/creating-new.md)  
 [Tabulka formátování číselných výsledků](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
