---
title: Jak zjistit, jestli řetězec představuje číselnou hodnotu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 5eda9684c6b9d376eeaa498e4c4adf4af2921e2e
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635090"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Jak zjistit, zda řetězec představuje číselnou hodnotu (C# Průvodce programováním)
Chcete-li určit, zda je řetězec platnou reprezentací zadaného číselného typu, použijte metodu static `TryParse`, která je implementována všemi primitivními číselnými typy a také podle typů, jako je <xref:System.DateTime> a <xref:System.Net.IPAddress>. Následující příklad ukazuje, jak určit, zda je "108" platný [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
```csharp  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Pokud řetězec obsahuje nenumerické znaky nebo číselná hodnota je příliš velká nebo příliš malá pro konkrétní typ, který jste zadali, `TryParse` vrátí hodnotu false a nastaví výstupní parametr na hodnotu nula. V opačném případě vrátí hodnotu true a nastaví výstupní parametr na číselnou hodnotu řetězce.  
  
> [!NOTE]
> Řetězec může obsahovat pouze číselné znaky a stále není platný pro typ, jehož `TryParse` metoda, kterou používáte. Například "256" není platná hodnota pro `byte`, ale je platná pro `int`. "98,6" není platná hodnota pro `int`, ale jedná se o platný `decimal`.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak použít `TryParse` s řetězcovými reprezentacemi `long`, `byte`a `decimal` hodnot.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Primitivní číselné typy také implementují metodu `Parse` static, která vyvolá výjimku, pokud řetězec není platným číslem. `TryParse` je všeobecně efektivnější, protože vrací hodnotu false pouze v případě, že je číslo neplatné.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pro ověření vstupu uživatele z ovládacích prvků, jako jsou textová pole a pole se seznamem, vždy použijte metody `TryParse` nebo `Parse`.  
  
## <a name="see-also"></a>Viz také:

- [Postup převodu pole bajtů na typ int](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Jak převést řetězec na číslo](../types/how-to-convert-a-string-to-a-number.md)
- [Jak převádět mezi hexadecimálními řetězci a číselnými typy](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analýza číselných řetězců](../../../standard/base-types/parsing-numeric.md)
- [Typy formátování](../../../standard/base-types/formatting-types.md)
