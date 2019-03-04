---
title: CType – funkce (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: dbf01263723a9e2890dab57d5ffc3d467ed250fc
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212050"
---
# <a name="ctype-function-visual-basic"></a>CType – funkce (Visual Basic)

Vrátí výsledek explicitně převedeného výrazu na zadaný datový typ, objekt, strukturu, třídu nebo rozhraní.

## <a name="syntax"></a>Syntaxe

```
CType(expression, typename)
```

## <a name="parts"></a>Součásti

`expression` Libovolný platný výraz. Pokud hodnota `expression` je mimo povolený rozsah povolený `typename`, Visual Basic vyvolá výjimku.

`typename` Libovolný výraz, který je platný v rámci `As` klauzule `Dim` příkazu, to znamená, že název všechny datový typ, objekt, strukturu, třídu nebo rozhraní.

## <a name="remarks"></a>Poznámky

> [!TIP]
> K provedení převodu typu můžete také použít následující funkce:
>
> - Například zadejte funkce pro převod `CByte`, `CDbl`, a `CInt` , které provádí převod na určitý datový typ. Další informace najdete v tématu [funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md).
> - [DirectCast – operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) nebo [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md). Tyto operátory vyžadují dědit z jednoho typu nebo implementaci druhého typu. Poskytují poněkud vyšší výkon než `CType` při převodu do a z `Object` datového typu.

`CType` je zkompilovaný vloženě, což znamená, že kód převodu je součástí kódu, který se vyhodnotí výraz. V některých případech kód běží rychleji, protože nejsou volány žádné procedury k provedení převodu.

Pokud není definován žádný převod z `expression` k `typename` (např. z `Integer` k `Date`), Visual Basic zobrazí zprávu Chyba kompilace.

Pokud převod selže v době běhu, je vyvolána vhodná výjimka. Pokud selže zužující převod <xref:System.OverflowException> je nejčastěji výsledkem. Pokud převod není definován, <xref:System.InvalidCastException> v vyvolána. Například to může nastat, když `expression` je typu `Object` a jeho typ za běhu nemá převod do `typename`.

Pokud datový typ `expression` nebo `typename` je třída nebo struktura, které jste definovali, můžete definovat `CType` na této třídě nebo struktuře jako operátor převodu. Díky tomu `CType` fungovat jako *přetížený operátor*. Pokud to uděláte, můžete řídit chování převodu do a z třídy nebo struktury, včetně výjimek, které mohou být vyvolány.

## <a name="overloading"></a>Přetížení

`CType` Operátoru lze také přetížit ve třídě nebo struktuře definované mimo váš kód. Pokud váš kód převede do nebo z takové třídy nebo struktury, měli byste pochopit chování jeho `CType` operátor. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="converting-dynamic-objects"></a>Převod dynamických objektů

Uživatelem definované dynamickými konverzemi pomocí provádí převody typů dynamických objektů <xref:System.Dynamic.DynamicObject.TryConvert%2A> nebo <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> metody. Pokud pracujete s dynamickými objekty, použijte <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> metody pro převod dynamického objektu.

## <a name="example"></a>Příklad

V následujícím příkladu `CType` funkce převodu výrazu `Single` datového typu.

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

Další příklady najdete v tématu [implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).

## <a name="see-also"></a>Viz také:

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Převodní funkce](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Postupy: Definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Převod typů v rozhraní .NET Framework](../../../standard/base-types/type-conversion.md)
