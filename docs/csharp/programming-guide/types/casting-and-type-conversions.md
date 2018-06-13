---
title: Přetypování a převody typů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 0c17fc89d93bdbb01bdef7935e72f8a7d96b0a55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336554"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Přetypování a převody typů (Průvodce programováním v C#)
Protože C# je staticky zadali v době kompilace po proměnné je deklarovaná, nemůže být znovu deklarován nebo používat k ukládání hodnoty jiného typu, pokud je tento typ převést na typ proměnné. Není třeba žádný převod z celé číslo na libovolný libovolný řetězec. Proto po deklarovat `i` jako celé číslo, nelze přiřadit řetězec "Hello", jak je znázorněno v následujícím kódu.  
  
```csharp  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 Však může někdy musíte zkopírovat hodnotu do proměnné nebo metoda parametru jiného typu. Například můžete mít proměnná typu integer, které potřebujete předat do metody, jejichž parametr je zadán jako `double`. Nebo možná budete muset přiřadit proměnné třídy proměnné typu rozhraní. Tyto typy operací se nazývají *převody typu*. V jazyce C# můžete provést následující typy převody:  
  
-   **Implicitní převody**: žádné speciální syntaxe není nutná převod je typově bezpečný a žádná data se ztratí. Mezi příklady patří převody z menší na větší integrální typy a převody z odvozené třídy základní třídy.  
  
-   **Explicitní převody (přetypování)**: explicitní převody vyžadují operátor přetypování. Když při převodu dojít ke ztrátě informací, nebo při převodu se nemusí zdařit z jiných důvodů je potřeba přetypování.  Typické příklady zahrnují číselný převod na typ, který má menší přesnost nebo určený menším rozsahem a převod instance základní třídy odvozené třídy.  
  
-   **Uživatelem definované převody**: uživatelem definované převody provádí speciální metody, které můžete definovat povolit explicitní a implicitní převody mezi vlastní typy, které nemají relaci základní třída – odvozené třídy. Další informace najdete v tématu [operátory převodu](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).  
  
-   **Převody s pomocné třídy**: pro převod mezi nekompatibilní typy, jako je celá čísla a <xref:System.DateTime?displayProperty=nameWithType> objekty, nebo hexadecimální řetězce a pole bajtů, můžete použít <xref:System.BitConverter?displayProperty=nameWithType> třídy, <xref:System.Convert?displayProperty=nameWithType> třídy a `Parse`metody předdefinované číselné typy, jako například <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Další informace najdete v tématu [postupy: převedení pole bajtů na typ int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [postupy: převedení řetězce na číslo](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), a [postupy: převod mezi hexadecimálními řetězci a číselnými typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).  
  
## <a name="implicit-conversions"></a>Implicitní převody  
 Pro předdefinované číselnými typy implicitní převod můžete provést, když hodnota, která má být uložen můžete začlenit do proměnné bez se zkrátí nebo zaokrouhlen. Například proměnná typu [dlouho](../../../csharp/language-reference/keywords/long.md) (celé číslo na 8 bajtů) může ukládat všechny hodnoty, které [int](../../../csharp/language-reference/keywords/int.md) můžete ukládat (4 bajty v počítači 32bitová verze). V následujícím příkladu, kompilátor implicitně převede hodnotu na pravé straně typu `long` před přiřazením jeho `bigNum`.  
  
 [!code-csharp[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 Úplný seznam všech implicitních číselných převodů, najdete v části [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 U typů odkazu existuje vždy implicitní převod z třídy na některý z jeho přímý nebo nepřímý základní třídy nebo rozhraní. Žádné speciální syntaxe je nutné, protože do odvozené třídy vždy obsahuje všechny členy základní třídy.  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Explicitní převody  
 Ale pokud převod nelze provést bez riziko ztráty informací, kompilátor vyžaduje provedení explicitní převod, která se nazývá *přetypování*. Přetypování představuje způsob, kterou chcete provést převod a že jste si vědomi, že může dojít ke ztrátě dat. explicitně informuje o kompilátoru. Pokud chcete provést přetypování, zadejte typ, který se přetypování na v závorkách před hodnota nebo proměnná, která má být převeden. Tento program přetypování [dvojité](../../../csharp/language-reference/keywords/double.md) k [int](../../../csharp/language-reference/keywords/int.md). Program nebude kompilovat bez přetypování.  
  
 [!code-csharp[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 Seznam explicitních číselných převodů, které jsou povoleny, naleznete v části [explicitní číselné převody tabulky](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
 U typů odkazu se vyžaduje explicitní přetypování, pokud je potřeba převést na odvozený typ základní typ:  
  
```csharp  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 Přetypování operace mezi odkazové typy nezmění běhového typu podkladového objektu; změní pouze typ hodnoty, který se používá jako odkaz na tento objekt. Další informace najdete v tématu [polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Typ převodu výjimky za běhu  
 V některých převody typu odkaz nemůže kompilátor zjistit, zda přetypování budou platné. Je možné pro přetypování operaci, která správně zkompiluje selhání za běhu. Jak je znázorněno v následujícím příkladu, přetypovat typ, způsobí, že selže v době běhu <xref:System.InvalidCastException> vyvolání.  
  
 [!code-csharp[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 C# poskytuje [je](../../../csharp/language-reference/keywords/is.md) a [jako](../../../csharp/language-reference/keywords/as.md) operátory umožnit pro testování kompatibility před provedením ve skutečnosti přetypování. Další informace najdete v tématu [postupy: bezpečné přetypování pomocí jako a je operátory](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [() – operátor](../../../csharp/language-reference/operators/invocation-operator.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)  
 [implicit](../../../csharp/language-reference/keywords/implicit.md)  
 [Operátory převodu](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [Převod zobecněný typů](http://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada)  
 [Převod exportovaný typů](http://msdn.microsoft.com/library/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)  
 [Postupy: Převedení řetězce na číslo](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
