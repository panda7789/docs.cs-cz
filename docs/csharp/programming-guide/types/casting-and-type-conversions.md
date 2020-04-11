---
title: Převody odlitků a typů – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: ae8f18deff5e96d7e475df8814ad64b38d14d585
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121392"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Převody přetypování a typu (Průvodce programováním jazyka C#)

Protože C# je staticky zadán v době kompilace, po deklarované proměnné, nemůže být deklarována znovu nebo přiřazena hodnota jiného typu, pokud tento typ je implicitně převoditelný s typem proměnné. Například `string` nelze implicitně převést `int`na . Proto po deklarování `i` jako `int`, nelze přiřadit řetězec "Hello" k němu, jak ukazuje následující kód:
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 Někdy však může být nutné zkopírovat hodnotu do parametru proměnné nebo metody jiného typu. Můžete mít například integer ovou proměnnou, kterou potřebujete předat metodě, jejíž parametr je zadán jako `double`. Nebo může být nutné přiřadit proměnnou třídy proměnné typu rozhraní. Tyto druhy operací se nazývají *převody typu*. V c# můžete provádět následující druhy převodů:  
  
- **Implicitní převody**: Není vyžadována žádná speciální syntaxe, protože převod je typově bezpečný a žádná data nebudou ztracena. Příklady zahrnují převody z menších na větší integrální typy a převody z odvozených tříd na základní třídy.  
  
- **Explicitní převody (přetypování):** Explicitní převody vyžadují [výraz přetypování](../../language-reference/operators/type-testing-and-cast.md#cast-expression). Obsazení je vyžadováno v případě, že informace mohou být ztraceny v převodu nebo pokud převod nemusí být úspěšný z jiných důvodů. Mezi typické příklady patří číselný převod na typ, který má menší přesnost nebo menší rozsah, a převod instance základní třídy na odvozenou třídu.  
  
- **Uživatelem definované převody**: Uživatelem definované převody jsou prováděny speciálními metodami, které můžete definovat tak, aby bylo možné povolit explicitní a implicitní převody mezi vlastními typy, které nemají vztah třídy odvozené základní třídy. Další informace naleznete v [tématu User-defined operátory převodu](../../language-reference/operators/user-defined-conversion-operators.md).  
  
- **Převody s pomocnými třídami**: Chcete-li převést mezi <xref:System.DateTime?displayProperty=nameWithType> nekompatibilními typy, například celočíselnými a objekty, nebo <xref:System.BitConverter?displayProperty=nameWithType> šestnáctkovými řetězci a bajtovými poli, můžete použít třídu, třídu <xref:System.Convert?displayProperty=nameWithType> a `Parse` metody předdefinovaných číselných typů, například <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Další informace naleznete [v tématech Převod bajtového pole na int](./how-to-convert-a-byte-array-to-an-int.md), [Jak převést řetězec na číslo](./how-to-convert-a-string-to-a-number.md)a Jak [převést mezi šestnáctkovými řetězci a číselnými typy](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
  
## <a name="implicit-conversions"></a>Implicitní převody

 Pro předdefinované číselné typy implicitní převod lze provést, když hodnota, která má být uložena vejde do proměnné bez zkrácení nebo zaokrouhlení off. Pro integrální typy to znamená, že rozsah typu zdroje je správná podmnožina rozsahu pro cílový typ. Například proměnná typu [long](../../language-reference/builtin-types/integral-numeric-types.md) (64bitové celé číslo) může ukládat libovolnou hodnotu, kterou může ukládat [int](../../language-reference/builtin-types/integral-numeric-types.md) (32bitové celé číslo). V následujícím příkladu kompilátor implicitně převede hodnotu `num` vpravo na typ `bigNum` `long` před jeho přiřazením .  
  
 [!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]  
  
 Úplný seznam všech implicitních číselných konverzí naleznete v části [Implicitní číselné převody](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions) v článku [Předdefinované číselné převody.](../../language-reference/builtin-types/numeric-conversions.md)
  
 Pro typy odkazů implicitní převod vždy existuje z třídy do některé z jeho přímé nebo nepřímé základní třídy nebo rozhraní. Žádná speciální syntaxe není nutná, protože odvozená třída vždy obsahuje všechny členy základní třídy.  
  
```csharp
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Explicitní převody

 Pokud však převod nelze provést bez rizika ztráty informací, kompilátor vyžaduje, abyste provedli explicitní převod, který se nazývá *přetypování*. Přetypování je způsob, jak explicitně informovat kompilátor, který chcete provést převod a že jste si vědomi, že může dojít ke ztrátě dat. Chcete-li provést přetypování, zadejte typ, do kterého přetypujte, v závorce před hodnotou nebo proměnnou, která má být převedena. Následující program [přetypovává double](../../language-reference/builtin-types/floating-point-numeric-types.md) [na int](../../language-reference/builtin-types/integral-numeric-types.md). Program nebude kompilovat bez přetypování.  
  
 [!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]  
  
 Úplný seznam podporovaných explicitních číselných konverzí naleznete v části [Explicitní číselné převody](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) v článku [Předdefinované číselné konverze.](../../language-reference/builtin-types/numeric-conversions.md)
  
 Pro typy odkazů je vyžadován explicitní přetypování, pokud potřebujete převést ze základního typu na odvozený typ:  
  
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
  
 Operace přetypování mezi typy odkazů nezmění typ běhu podkladového objektu; změní pouze typ hodnoty, která se používá jako odkaz na tento objekt. Další informace naleznete [v tématu Polymorfismus](../classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Zadejte výjimky převodu za běhu

 V některých převodech typu odkazu kompilátor nemůže určit, zda bude přetypování platné. Je možné pro přetypování operace, která zkompiluje správně nezdaří v době běhu. Jak je znázorněno v následujícím příkladu, přetypovaného typu, který selže v době běhu způsobí, <xref:System.InvalidCastException> že vyvolá.  
  
 [!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]  
  
 C# poskytuje [je](../../language-reference/operators/type-testing-and-cast.md#is-operator) operátor, který vám umožní otestovat kompatibilitu před skutečně provedení přetypování. Další informace naleznete v tématu [Jak bezpečně přetypování pomocí porovnávání vzorů a as a is operátory](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).  
  
## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Převody](~/_csharplang/spec/conversions.md) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Typy](./index.md)
- [Výraz přetypování](../../language-reference/operators/type-testing-and-cast.md#cast-expression)
- [Operátory převodu definované uživatelem](../../language-reference/operators/user-defined-conversion-operators.md)
- [Převod zobecněného typu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))
- [Jak převést řetězec na číslo](./how-to-convert-a-string-to-a-number.md)
