---
title: Přetypování a převody typu – C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 8753e977007e46ea4227c8c0072671a2e9298645
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362129"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Přetypování a převody typu (C# Programming Guide)

C# je staticky typovaný v době kompilace, jakmile je proměnná deklarována, nemůže být znovu deklarován nebo mu přiřazena hodnota jiného typu, pokud je tento typ implicitně převést na typ proměnné. Například `string` nejde implicitně převést na `int`. Proto po deklarování `i` jako `int`, nelze přiřadit řetězec "Hello", jak ukazuje následující kód:
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 Však můžete někdy potřebovat zkopírovat hodnotu do proměnné nebo metody parametr jiného typu. Například můžete mít celočíselnou proměnnou, která je potřeba předat metodě, jehož parametr zadán jako `double`. Nebo možná budete muset proměnné třídy přiřadit proměnné typu rozhraní. Tyto typy operací jsou volány *převody typů*. V jazyce C# můžete provést následující druhy převody:  
  
-   **Implicitní převody**: Žádná speciální syntax není nutná, protože převod je typově bezpečný a žádná data se ztratí. Mezi příklady patří převody z menších na větší celočíselné typy a převody z odvozené třídy základní třídy.  
  
-   **Explicitní převody (přetypování)**: Explicitní převody vyžadují operátor přetypování. Přetypování je povinný při převodu dojít ke ztrátě informací nebo při převodu se nemusí zdařit z jiných důvodů.  Typické příklady zahrnují číselný převod na typ, který má nižší přesnost nebo menší rozsah a převodu instance základní třídy na odvozenou třídu.  
  
-   **Uživatelem definované převody**: Uživatelem definované převody jsou prováděny speciální metody, které můžete definovat umožňuje explicitní a implicitní převody mezi vlastní typy, které nemají vztah základní třídy – odvozených tříd. Další informace najdete v tématu [operátory převodu](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).  
  
-   **Převod pomocí tříd pomocných rutin**: K převodu mezi nekompatibilními typy, jako jsou celá čísla a <xref:System.DateTime?displayProperty=nameWithType> objektů, nebo hexadecimálními řetězci a bajtová pole, můžete použít <xref:System.BitConverter?displayProperty=nameWithType> třídy, <xref:System.Convert?displayProperty=nameWithType> třídy a `Parse` metody předdefinované číselné typy, jako <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Další informace najdete v tématu [jak: Převedení pole bajtů na typ int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [jak: Převod řetězce na číslo](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), a [jak: Převod mezi hexadecimálními řetězci a číselnými typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).  
  
## <a name="implicit-conversions"></a>Implicitní převody

 Pro předdefinované číselné typy implicitní převod může vzít v úvahu hodnota, která má být uložen se vejde do proměnné bez zkrácen nebo zaokrouhleno. Například proměnná typu [dlouhé](../../../csharp/language-reference/keywords/long.md) (64bitové celé číslo) můžete ukládat některá hodnota, která [int](../../../csharp/language-reference/keywords/int.md) (32bitové celé číslo) můžete ukládat. V následujícím příkladu kompilátor implicitně převede hodnotu `num` na pravé straně na typ `long` před ji přiřadíte `bigNum`.  
  
 [!code-csharp[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 Úplný seznam všech implicitních číselných převodů, naleznete v tématu [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Pro typy odkazů existuje vždy implicitní převod z třídy na některý z jeho přímou nebo nepřímou základní třídy nebo rozhraní. Žádná speciální syntax je nezbytné, protože odvozené třídy vždy obsahuje všechny členy základní třídy.  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Explicitní převody

 Nicméně, pokud převod nelze provést bez rizika ztráty informací, kompilátor vyžaduje, abyste provedli explicitní převod, která je volána *přetypování*. Přetypování je způsob, jak explicitně informuje kompilátor, že máte v úmyslu provést převod a že jste si vědomi, že může dojít ke ztrátě dat. K provedení přetypování, zadejte, která jsou přetypování na typ v závorkách před hodnota nebo proměnná, která má být převeden. Následující program přetypování [double](../../../csharp/language-reference/keywords/double.md) do [int](../../../csharp/language-reference/keywords/int.md). Program nebude kompilovat bez přetypování.  
  
 [!code-csharp[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 Seznam explicitních číselných převodů, které jsou povoleny, naleznete v tématu [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
 Pro typy odkazů se vyžaduje explicitní přetypování, pokud je potřeba převést ze základního typu odvozeného typu:  
  
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
  
 Operace přetypování mezi typy odkazů nezmění běhového typu základního objektu; pouze změní typ hodnoty, který se používá jako odkaz na tento objekt. Další informace najdete v tématu [polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Typ převodu výjimky za běhu

 V některých převodům typu odkaz kompilátor nemůže určit, zda bude platit přetypování. Je možné pro operace přetypování, které se správně zkompiluje selže v době běhu. Jak je znázorněno v následujícím příkladu, typu přetypování, že selže v době běhu způsobí, že <xref:System.InvalidCastException> vyvolání.  
  
 [!code-csharp[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 Jazyk C# poskytuje [je](../../../csharp/language-reference/keywords/is.md) a [jako](../../../csharp/language-reference/keywords/as.md) operátory umožňující testování kompatibility ve skutečnosti neodkazujícím přetypování. Další informace najdete v tématu [jak: Bezpečné přetypování pomocí porovnávání vzorů, jako je operátory](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).  
  
## <a name="c-language-specification"></a>specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Typy](../../../csharp/programming-guide/types/index.md)  
- [() – operátor](../../../csharp/language-reference/operators/invocation-operator.md)  
- [explicit](../../../csharp/language-reference/keywords/explicit.md)  
- [implicit](../../../csharp/language-reference/keywords/implicit.md)  
- [Operátory převodu](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
- [Převod zobecněného typu](https://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada)  
- [Převod exportovaného typu](https://msdn.microsoft.com/library/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)  
- [Postupy: Převod řetězce na číslo](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
