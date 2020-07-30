---
title: Jak zjistit, zda řetězec představuje číselnou hodnotu – Průvodce programováním v C#
description: Zjistěte, jak zjistit, zda je řetězec platnou reprezentací zadaného číselného typu. Podívejte se na příklady kódu a zobrazte další prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: c248c6c54de493ab06a833fc525252fa812d60da
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381746"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Jak zjistit, zda řetězec představuje číselnou hodnotu (Průvodce programováním v C#)
Chcete-li zjistit, zda je řetězec platnou reprezentací zadaného číselného typu, použijte statickou `TryParse` metodu, která je implementována všemi primitivními číselnými typy a také podle typů, jako jsou <xref:System.DateTime> a <xref:System.Net.IPAddress> . Následující příklad ukazuje, jak určit, zda je "108" platný [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Pokud řetězec obsahuje nenumerické znaky nebo číselná hodnota je pro konkrétní typ, který jste zadali, příliš velká nebo příliš malá, `TryParse` vrátí hodnotu false a nastaví výstupní parametr na hodnotu nula. V opačném případě vrátí hodnotu true a nastaví výstupní parametr na číselnou hodnotu řetězce.  
  
> [!NOTE]
> Řetězec může obsahovat pouze číselné znaky a stále není platný pro typ `TryParse` , jehož metodu používáte. Například "256" není platná hodnota, `byte` ale je platná pro `int` . "98,6" není platná hodnota `int` , ale je platná `decimal` .  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak používat `TryParse` s řetězcovými reprezentacemi `long` `byte` hodnot, a `decimal` .  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Primitivní číselné typy také implementují `Parse` statickou metodu, která vyvolá výjimku, pokud řetězec není platným číslem. `TryParse`je všeobecně efektivnější, protože vrací hodnotu false pouze v případě, že je číslo neplatné.  
  
## <a name="net-security"></a>Zabezpečení .NET  
 Vždy použijte `TryParse` metody nebo `Parse` k ověření vstupu uživatele z ovládacích prvků, jako jsou textová pole a pole se seznamem.  
  
## <a name="see-also"></a>Viz také:

- [Jak převést pole bajtů na celé číslo](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Jak převést řetězec na číslo](../types/how-to-convert-a-string-to-a-number.md)
- [Jak převádět mezi hexadecimálními řetězci a číselnými typy](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analýza číselných řetězců](../../../standard/base-types/parsing-numeric.md)
- [Typy formátování](../../../standard/base-types/formatting-types.md)
