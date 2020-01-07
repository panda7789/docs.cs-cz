---
title: Přetypování a převody typů C# – Průvodce programováním
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
ms.openlocfilehash: 7285b69ea34be087705c1163a94310d43b2f6f02
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635064"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Přetypování a převody typůC# (Průvodce programováním)

Vzhledem C# k tomu, že je staticky zadán v době kompilace, poté, co je deklarována proměnná, nelze ji deklarovat znovu ani přiřadit hodnotu jiného typu, pokud tento typ není implicitně převeden na typ proměnné. `string` například nelze implicitně převést na `int`. Proto po deklaraci `i` jako `int`nemůžete k ní přiřadit řetězec "Hello", jak ukazuje následující kód:
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 Někdy však může být nutné zkopírovat hodnotu do proměnné nebo parametru metody jiného typu. Například můžete mít celočíselnou proměnnou, kterou potřebujete předat metodě, jejíž parametr je zadán jako `double`. Nebo může být nutné přiřadit proměnnou třídy proměnné typu rozhraní. Tyto druhy operací se nazývají *převody typu*. V C#nástroji můžete provádět následující typy převodů:  
  
- **Implicitní převody**: nevyžaduje se žádná speciální syntaxe, protože převod je typově bezpečný a neztratí se žádná data. Příklady zahrnují převody z menších na větší integrální typy a převody z odvozených tříd na základní třídy.  
  
- **Explicitní převody (přetypování)** : explicitní převody vyžadují [operátor přetypování `()`](../../language-reference/operators/type-testing-and-cast.md#cast-operator-). Přetypování je požadováno v případě, že může dojít ke ztrátě informací v převodu nebo v případě, že převod nemusí být úspěšný z jiných důvodů. Mezi typické příklady patří číselný převod na typ, který má menší přesnost nebo menší rozsah, a převod instance základní třídy na odvozenou třídu.  
  
- **Uživatelem definované převody**: uživatelsky definované převody jsou prováděny speciálními metodami, které můžete definovat pro povolení explicitních a implicitních převodů mezi vlastními typy, které nemají základní třídu odvozenou od atributu Base Class. Další informace naleznete v tématu [uživatelsky definované operátory převodu](../../language-reference/operators/user-defined-conversion-operators.md).  
  
- **Převody s podpůrnými třídami**: pro převod mezi nekompatibilními typy, jako jsou například celá čísla a <xref:System.DateTime?displayProperty=nameWithType> objekty nebo hexadecimální řetězce a pole bajtů, lze použít třídu <xref:System.BitConverter?displayProperty=nameWithType>, třídu <xref:System.Convert?displayProperty=nameWithType> a metody `Parse` předdefinovaných číselných typů, jako je například <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Další informace naleznete v tématu [Jak převést bajtové pole na int](./how-to-convert-a-byte-array-to-an-int.md), [Jak převést řetězec na číslo](./how-to-convert-a-string-to-a-number.md)a [Jak převádět mezi hexadecimálními řetězci a číselnými typy](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
  
## <a name="implicit-conversions"></a>Implicitní převody

 U předdefinovaných číselných typů lze vytvořit implicitní převod, pokud hodnota, která má být uložena, se může vejít do proměnné, aniž by byla zkrácena nebo zaokrouhlena. U integrálních typů to znamená, že rozsah zdrojového typu je správná podmnožina rozsahu pro cílový typ. Například proměnná typu [Long](../../language-reference/builtin-types/integral-numeric-types.md) (64-bit integer) může ukládat libovolnou hodnotu, kterou může [Uložit celé číslo (32](../../language-reference/builtin-types/integral-numeric-types.md) ). V následujícím příkladu kompilátor implicitně převede hodnotu `num` na pravé straně k typu `long` před přiřazením do `bigNum`.  
  
 [!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]  
  
 Úplný seznam všech implicitních převodů čísel najdete v části [implicitní číselné převody](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions) v tématu [integrovaných číselných převodů](../../language-reference/builtin-types/numeric-conversions.md) .
  
 U typů odkazů je implicitní převod vždy existovat ze třídy na jakoukoli z přímých nebo nepřímých základních tříd nebo rozhraní. Žádná speciální syntaxe není nutná, protože odvozená třída vždy obsahuje všechny členy základní třídy.  
  
```csharp
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Explicitní převody

 Nicméně, pokud převod nelze provést bez rizika ztráty informací, kompilátor vyžaduje, abyste provedli explicitní převod, který se nazývá *přetypování*. Přetypování je způsob, jak explicitně informovat kompilátor, který máte v úmyslu převést, a že víte, že by mohlo dojít ke ztrátě dat. Chcete-li provést přetypování, zadejte typ, na který se předáváte, do závorek před hodnotu nebo proměnnou, která má být převedena. Následující program přetypování [Double](../../language-reference/builtin-types/floating-point-numeric-types.md) na [int](../../language-reference/builtin-types/integral-numeric-types.md). Program nebude zkompilován bez přetypování.  
  
 [!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]  
  
 Úplný seznam podporovaných explicitních převodů naleznete v části [explicitní číselné převody](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) v tématu [integrovaných číselných převodů](../../language-reference/builtin-types/numeric-conversions.md) .
  
 U typů odkazů je vyžadováno explicitní přetypování, pokud potřebujete převést ze základního typu na odvozený typ:  
  
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
  
 Operace přetypování mezi typy odkazů nemění typ běhu podkladového objektu; změní jenom typ hodnoty, která se používá jako odkaz na tento objekt. Další informace najdete v tématu [polymorfismus](../classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Výjimky převodu typů v době běhu

 V některých převodech typu reference kompilátor nemůže určit, zda bude přetypování platné. Je možné, že operace přetypování, která se správně zkompiluje, aby selhala v době běhu. Jak je znázorněno v následujícím příkladu, přetypování, které selže v době běhu, způsobí vyvolání <xref:System.InvalidCastException>.  
  
 [!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]  
  
 C#poskytuje operátor [is](../../language-reference/operators/type-testing-and-cast.md#is-operator) , který umožňuje testovat kompatibilitu před samotným přetypováním. Další informace naleznete v tématu [jak bezpečně přetypovat pomocí porovnávání vzorů a operátorů as a is](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).  
  
## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [převody](~/_csharplang/spec/conversions.md) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Typy](./index.md)
- [() cast – operátor](../../language-reference/operators/type-testing-and-cast.md#cast-operator-)
- [Uživatelsky definované operátory převodu](../../language-reference/operators/user-defined-conversion-operators.md)
- [Převod generalizované typu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))
- [Jak převést řetězec na číslo](./how-to-convert-a-string-to-a-number.md)
