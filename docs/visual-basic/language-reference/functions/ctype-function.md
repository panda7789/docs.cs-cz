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
ms.openlocfilehash: 4a0391b0a5d76f36803b433369d4832c02b05e09
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592101"
---
# <a name="ctype-function-visual-basic"></a>CType – funkce (Visual Basic)

Vrátí výsledek explicitního převodu výrazu na zadaný datový typ, objekt, strukturu, třídu nebo rozhraní.

## <a name="syntax"></a>Syntaxe

```vb
CType(expression, typename)
```

## <a name="parts"></a>Součásti

@no__t – 0 libovolný platný výraz. Pokud je hodnota `expression` mimo rozsah povolený `typename`, Visual Basic vyvolá výjimku.

@no__t – 0 libovolný výraz, který je platný v rámci klauzule `As` v příkazu `Dim`, to znamená název libovolného datového typu, objektu, struktury, třídy nebo rozhraní.

## <a name="remarks"></a>Poznámky

> [!TIP]
> K provedení převodu typu můžete použít taky následující funkce:
>
> - Funkce pro převod typů, například `CByte`, `CDbl` a `CInt`, které provádějí převod na konkrétní datový typ. Další informace najdete v tématu [funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md).
> - [Operátor DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) nebo [operátor TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) Tyto operátory vyžadují, aby jeden typ dědil z nebo implementoval jiný typ. Při převodu do a z datového typu `Object` mohou poskytovat poněkud lepší výkon než `CType`.

`CType` je kompilováno jako inline, což znamená, že kód převodu je součástí kódu, který vyhodnocuje výraz. V některých případech kód běží rychleji, protože pro provedení převodu nejsou volány žádné procedury.

Pokud není definován žádný převod z `expression` na `typename` (například z `Integer` na `Date`), Visual Basic zobrazí chybovou zprávu při kompilaci.

Pokud se převod v době běhu nezdařil, je vyvolána příslušná výjimka. Pokud se nezdařil převod, je <xref:System.OverflowException> nejběžnějším výsledkem. Pokud převod není definován, <xref:System.InvalidCastException> v vyvolání. K tomu může dojít například v případě, že `expression` je typu `Object` a jeho typ za běhu nemá žádný převod na `typename`.

Pokud je datový typ `expression` nebo `typename` třídou nebo strukturou, kterou jste definovali, můžete definovat `CType` v této třídě nebo struktuře jako operátor převodu. Díky tomu `CType` fungovat jako *přetížený operátor*. Pokud to uděláte, můžete řídit chování převodu do a z vaší třídy nebo struktury, včetně výjimek, které mohou být vyvolány.

## <a name="overloading"></a>Přetížení

Operátor `CType` lze také přetížit pro třídu nebo strukturu definovanou mimo váš kód. Pokud se váš kód převede na nebo z takové třídy nebo struktury, ujistěte se, že rozumíte chování operátoru `CType`. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="converting-dynamic-objects"></a>Převod dynamických objektů

Převody typů dynamických objektů jsou prováděny uživatelsky definovanými dynamickými převody, které používají metody <xref:System.Dynamic.DynamicObject.TryConvert%2A> nebo <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>. Pokud pracujete s dynamickými objekty, použijte metodu <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> pro převod dynamického objektu.

## <a name="example"></a>Příklad

Následující příklad používá funkci `CType` k převodu výrazu na datový typ `Single`.

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

Další příklady naleznete v tématu [implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).

## <a name="see-also"></a>Viz také:

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Převodní funkce](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Postupy: Definovat operátor převodu @ no__t-0
- [Převod typu v .NET Framework](../../../standard/base-types/type-conversion.md)
