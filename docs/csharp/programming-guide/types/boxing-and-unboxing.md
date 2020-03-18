---
title: Průvodce zabalením a rozbalením – programovací příručka jazyka C#
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 62df08bf4ae3580e9b8d5b3aab0697d396674ca1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745410"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Zabalení a rozbalení (Průvodce programováním v C#)

Zabalení je proces převodu [typu](../../language-reference/builtin-types/value-types.md) hodnoty `object` na typ nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty. Když běžný jazyk runtime (CLR) krabice typ hodnoty, zalomí hodnotu uvnitř <xref:System.Object?displayProperty=nameWithType> instance a uloží ji na spravované haldy. Rozbalení extrahuje typ hodnoty z objektu. Box je implicitní; rozbalení je explicitní. Koncept zabalení a rozbalení je základem jednotného zobrazení c# systému typů, ve kterém lze hodnotu libovolného typu považovat za objekt.

V následujícím příkladu je celá `i` proměnná *zabalena* `o`a přiřazena k objektu .

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

Objekt `o` pak může být unboxed a přiřazené k celé číslo proměnné `i`:

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

Následující příklady ilustrují, jak se zabalení používá v c#.

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a>Výkon

Ve vztahu k jednoduchým přiřazením jsou zabalení a rozbalení výpočtově nákladné procesy. Pokud je typ hodnoty zabalen, musí být přidělen a vytvořen nový objekt. V menší míře je obsazení potřebné pro rozbalení také nákladné výpočtově. Další informace naleznete v tématu [Performance](../../../framework/performance/performance-tips.md).

## <a name="boxing"></a>Zabalení

Zabalení se používá k ukládání typů hodnot v haldě uvolňování paměti. Zabalení je implicitní převod [typu](../../language-reference/builtin-types/value-types.md) `object` hodnoty na typ nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty. Zabalení typu hodnoty přidělí instanci objektu na haldě a zkopíruje hodnotu do nového objektu.

Zvažte následující deklaraci proměnné typu hodnoty:

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

Následující příkaz implicitně použije operaci zabalení `i`proměnné :

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

Výsledkem tohoto příkazu je `o`vytvoření odkazu na objekt , v zásobníku, který odkazuje na hodnotu typu `int`, na haldě. Tato hodnota je kopií hodnoty typu hodnoty přiřazené proměnné `i`. Rozdíl mezi těmito dvěma proměnnými `i` a `o`, je znázorněn na následujícím obrázku převodu zabalení:

![Obrázek znázorňující rozdíl mezi proměnnými i a o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

Je také možné provést zabalení explicitně jako v následujícím příkladu, ale explicitní zabalení není nikdy vyžadováno:

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a>Popis

Tento příklad převede celou `i` proměnnou `o` na objekt pomocí zabalení. Poté se hodnota uložená `i` v `123` proměnné `456`změní z na . Příklad ukazuje, že původní typ hodnoty a zabalený objekt používají samostatná umístění paměti, a proto mohou ukládat různé hodnoty.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a>Unboxing

Rozbalení je explicitní převod `object` z typu na [typ hodnoty](../../language-reference/builtin-types/value-types.md) nebo z typu rozhraní na typ hodnoty, který implementuje rozhraní. Operace rozbalení se skládá z:

- Kontrola instance objektu a ujistěte se, že se jedná o zabalenou hodnotu daného typu hodnoty.

- Kopírování hodnoty z instance do proměnné typu hodnoty.

Následující příkazy ukazují operace zabalení i rozbalení:

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

Následující obrázek ukazuje výsledek předchozích prohlášení:

![Obrázek znázorňující převod rozbalení.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

Pro unboxing typů hodnot úspěšné za běhu, musí být položka, která je unboxed odkaz na objekt, který byl dříve vytvořen zabalením instance tohoto typu hodnoty. Pokus o zrušení `null` rozesbalení způsobí. <xref:System.NullReferenceException> Pokus o zrušení pole odkazu na nekompatibilní <xref:System.InvalidCastException>typ hodnoty způsobí, že .

## <a name="example"></a>Příklad

Následující příklad ukazuje případ neplatné unboxing a `InvalidCastException`výsledné . Použití `try` `catch`a , zobrazí se chybová zpráva, když dojde k chybě.

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

Tento program vyvodí:

`Specified cast is not valid. Error: Incorrect unboxing.`

Pokud změníte příkaz:

```csharp
int j = (short) o;
```

na:

```csharp
int j = (int) o;
```

konverze bude provedena, a dostanete výstup:

`Unboxing OK.`

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Referenční typy](../../language-reference/keywords/reference-types.md)
- [Typy hodnot](../../language-reference/builtin-types/value-types.md)
