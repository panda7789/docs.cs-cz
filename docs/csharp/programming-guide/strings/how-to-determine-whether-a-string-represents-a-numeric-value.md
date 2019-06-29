---
title: 'Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 626fce590ba08bbdabf27ac33287a0b46b592f9c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423619"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu (C# Průvodce programováním v)
Chcete-li zjistit, zda je řetězec reprezentaci platná zadané číselného typu, použijte statické `TryParse` metodu, která je implementována všechny primitivní číselné typy a také typy, jako <xref:System.DateTime> a <xref:System.Net.IPAddress>. Následující příklad ukazuje, jak zjistit, jestli "108" je platný [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md).  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Pokud řetězec obsahuje znaky číselného typu nebo číselná hodnota je příliš velký či příliš malý pro konkrétní typ, který jste zadali, `TryParse` vrátí hodnotu false a nastaví výstupní parametr na hodnotu nula. V opačném případě vrátí hodnotu true a nastaví výstupní parametr na číselnou hodnotu řetězce.  
  
> [!NOTE]
>  Řetězec může obsahovat pouze číselné znaky a stále není možné pro daný typ platná jehož `TryParse` metodu, která používáte. Například "256" není platná hodnota pro `byte` , ale je platný pro `int`. "98.6" není platná hodnota pro `int` je platný, ale `decimal`.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak používat `TryParse` s řetězcové reprezentace `long`, `byte`, a `decimal` hodnoty.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Primitivní číselné typy i implementace `Parse` statická metoda, která vyvolá výjimku, pokud řetězec není platné číslo. `TryParse` je obecně efektivnější, protože se právě vrací hodnotu false, pokud číslo není platné.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vždy používat `TryParse` nebo `Parse` metody k ověření uživatelského vstupu z ovládacích prvků, jako je například textová pole a pole se seznamem.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Převedení pole bajtů na typ int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)
- [Postupy: Převod řetězce na číslo](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
- [Postupy: Převod mezi hexadecimálními řetězci a číselnými typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analýza číselných řetězců](../../../standard/base-types/parsing-numeric.md)
- [Typy formátování](../../../standard/base-types/formatting-types.md)
