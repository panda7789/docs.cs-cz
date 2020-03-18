---
title: Jak zjistit, zda řetězec představuje číselnou hodnotu - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 15a21a6298f8f0a57e0189554246202b220dd259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157062"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Jak zjistit, zda řetězec představuje číselnou hodnotu (Průvodce programováním jazyka C#)
Chcete-li zjistit, zda je řetězec platnou reprezentací zadaného číselného typu, použijte `TryParse` statickou <xref:System.DateTime> <xref:System.Net.IPAddress>metodu, která je implementována všemi primitivními číselnými typy a také typy, jako je například a . Následující příklad ukazuje, jak zjistit, zda "108" je platný [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Pokud řetězec obsahuje nečíselné znaky nebo číselná hodnota je příliš velká `TryParse` nebo příliš malá pro konkrétní typ, který jste zadali, vrátí hodnotu false a nastaví parametr out na nulu. V opačném případě vrátí hodnotu true a nastaví parametr out na číselnou hodnotu řetězce.  
  
> [!NOTE]
> Řetězec může obsahovat pouze číselné znaky a `TryParse` stále není platný pro typ, jehož metodu používáte. Například "256" není platná hodnota `byte` pro, ale `int`je platný pro . "98.6" není platná hodnota, `int` ale je `decimal`platná .  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, `TryParse` jak se používat `long` `byte`s `decimal` řetězcovými reprezentacemi , a hodnot.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Primitivní číselné typy `Parse` také implementovat statickou metodu, která vyvolá výjimku, pokud řetězec není platné číslo. `TryParse`je obecně efektivnější, protože pouze vrátí false, pokud číslo není platné.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vždy použijte `TryParse` `Parse` metody or k ověření vstupu uživatele z ovládacích prvků, jako jsou textová pole a pole se seznamem.  
  
## <a name="see-also"></a>Viz také

- [Jak převést pole bajtů na celé číslo](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Jak převést řetězec na číslo](../types/how-to-convert-a-string-to-a-number.md)
- [Jak převádět mezi hexadecimálními řetězci a číselnými typy](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analýza číselných řetězců](../../../standard/base-types/parsing-numeric.md)
- [Typy formátování](../../../standard/base-types/formatting-types.md)
