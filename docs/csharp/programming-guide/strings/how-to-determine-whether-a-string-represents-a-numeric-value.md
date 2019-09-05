---
title: 'Postupy: Určení, zda řetězec představuje číselnou hodnotu – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 8fc5051893882a6dbdbb4c9097949794d4430a93
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252956"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Postupy: Určení, zda řetězec představuje číselnou hodnotu (C# Průvodce programováním)
Chcete-li zjistit, zda je řetězec platnou reprezentací zadaného číselného typu, použijte statickou `TryParse` metodu, která je implementována všemi primitivními číselnými typy a také podle <xref:System.DateTime> typů <xref:System.Net.IPAddress>, jako jsou a. Následující příklad ukazuje, jak určit, zda je "108" platný [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
```csharp  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Pokud řetězec obsahuje nenumerické znaky nebo číselná hodnota je pro konkrétní typ, který jste zadali, příliš velká nebo příliš malá, `TryParse` vrátí hodnotu false a nastaví výstupní parametr na hodnotu nula. V opačném případě vrátí hodnotu true a nastaví výstupní parametr na číselnou hodnotu řetězce.  
  
> [!NOTE]
> Řetězec může obsahovat pouze číselné znaky a stále není platný pro typ, jehož `TryParse` metodu používáte. Například "256" není platná hodnota `byte` , ale je platná pro. `int` "98,6" není platná hodnota `int` , ale je platná. `decimal`  
  
## <a name="example"></a>Příklad  
 Následující `TryParse` příklady ukazují `long`, jak používat s řetězcovými reprezentacemi hodnot, `byte`a `decimal` .  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Primitivní číselné typy také implementují `Parse` statickou metodu, která vyvolá výjimku, pokud řetězec není platným číslem. `TryParse`je všeobecně efektivnější, protože vrací hodnotu false pouze v případě, že je číslo neplatné.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vždy použijte `TryParse` metody nebo `Parse` k ověření vstupu uživatele z ovládacích prvků, jako jsou textová pole a pole se seznamem.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Převod bajtového pole na int](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Postupy: Převést řetězec na číslo](../types/how-to-convert-a-string-to-a-number.md)
- [Postupy: Převod mezi hexadecimálními řetězci a číselnými typy](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analýza číselných řetězců](../../../standard/base-types/parsing-numeric.md)
- [Typy formátování](../../../standard/base-types/formatting-types.md)
