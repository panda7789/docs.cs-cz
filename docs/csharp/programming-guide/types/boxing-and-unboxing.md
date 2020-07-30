---
title: Zabalení a rozbalení – Průvodce programováním v C#
description: Přečtěte si o zabalení a rozbalení v programování v jazyce C#. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 5a5bfcc79de8ba3ff66ca8aab9d86d69d89f9221
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380693"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Zabalení a rozbalení (Průvodce programováním v C#)

Zabalení je proces převodu [typu hodnoty](../../language-reference/builtin-types/value-types.md) na typ `object` nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty. Když pole modulu CLR (Common Language Runtime) obsahuje typ hodnoty, zabalí hodnotu uvnitř <xref:System.Object?displayProperty=nameWithType> instance a uloží ji na spravovanou haldu. Rozbalení extrahuje typ hodnoty z objektu. Zabalení je implicitní; rozbalení je explicitní. Pojem zabalení a rozbalení je základem sjednoceného zobrazení systému typů, ve kterém může být hodnota libovolného typu považována za objekt.

V následujícím příkladu je proměnná typu Integer `i` *zabalená* a přiřazená objektu `o` .

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

Objekt `o` pak může být nezabalený a přiřazený celočíselné proměnné `i` :

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

Následující příklady ilustrují, jak se používá zabalení v jazyce C#.

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a>Výkon

Ve vztahu k jednoduchým přiřazením se zabalení a rozbalení počítají jako výpočetní náročné procesy. Když je hodnotový typ v krabici, musí být přidělen a vytvořen nový objekt. V menší míře je přetypování vyžadované pro rozbalení také nákladné výpočetní. Další informace najdete v tématu [výkon](../../../framework/performance/performance-tips.md).

## <a name="boxing"></a>Zabalení

Zabalení se používá k ukládání typů hodnot v haldě uvolňování paměti. Zabalení je implicitní převod [typu hodnoty](../../language-reference/builtin-types/value-types.md) na typ `object` nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty. Zabalení typu hodnoty přiděluje instanci objektu na haldě a zkopíruje hodnotu do nového objektu.

Zvažte následující deklaraci proměnné typu hodnoty:

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

Následující příkaz implicitně aplikuje operaci zabalení na proměnnou `i` :

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

Výsledek tohoto příkazu vytváří odkaz `o` na objekt v zásobníku, který odkazuje na hodnotu typu `int` , na haldě. Tato hodnota je kopií hodnoty typu hodnoty přiřazené proměnné `i` . Rozdíl mezi dvěma proměnnými `i` a `o` , je znázorněno na následujícím obrázku převodu zabalení:

![Obrázek znázorňující rozdíl mezi proměnnými i a o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

Je také možné provést zabalení explicitně jako v následujícím příkladu, ale explicitní zabalení není nikdy vyžadováno:

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a>Popis

Tento příklad převede proměnnou celého čísla `i` na objekt `o` pomocí zabalení. Pak se hodnota uložená v proměnné `i` změní z `123` na `456` . Příklad ukazuje, že původní typ hodnoty a zabalený objekt používají oddělené umístění paměti, a proto může ukládat jiné hodnoty.

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a>Rozbalení

Rozbalení je explicitní převod z typu `object` na [typ hodnoty](../../language-reference/builtin-types/value-types.md) nebo z typu rozhraní na typ hodnoty, který implementuje rozhraní. Rozbalení operace se skládá z těchto:

- Kontrola instance objektu, aby se zajistilo, že se jedná o zabalenou hodnotu daného typu hodnoty.

- Zkopírování hodnoty z instance do proměnné typu hodnoty.

Následující příkazy ukazují operace zabalení a rozbalení:

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

Následující obrázek ukazuje výsledek předchozích příkazů:

![Obrázek znázorňující převod rozbalení](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

Pro rozbalení typů hodnot, které mají být v době běhu úspěšné, musí být položka unboxed odkaz na objekt, který byl dříve vytvořen zabalením instance daného typu hodnoty. Pokus o unbox `null` způsobí <xref:System.NullReferenceException> . Pokus o unbox odkazu na nekompatibilní typ hodnoty způsobí <xref:System.InvalidCastException> .

## <a name="example"></a>Příklad

Následující příklad ukazuje případ neplatného rozbalení a výsledného `InvalidCastException` . `try`Při použití a se `catch` zobrazí chybová zpráva, když dojde k chybě.

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

Výstup tohoto programu:

`Specified cast is not valid. Error: Incorrect unboxing.`

Pokud změníte příkaz:

```csharp
int j = (short) o;
```

na

```csharp
int j = (int) o;
```

provede se převod a zobrazí se výstup:

`Unboxing OK.`

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Odkazové typy](../../language-reference/keywords/reference-types.md)
- [Typy hodnot](../../language-reference/builtin-types/value-types.md)
