---
title: CType – funkce
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 88d609146648fe1b0c3124b99a65e85293fc0707
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406427"
---
# <a name="ctype-function-visual-basic"></a>CType – funkce (Visual Basic)

Vrátí výsledek explicitního převodu výrazu na zadaný datový typ, objekt, strukturu, třídu nebo rozhraní.

## <a name="syntax"></a>Syntaxe

```vb
CType(expression, typename)
```

## <a name="parts"></a>Součásti

`expression`Libovolný platný výraz. Pokud `expression` je hodnota mimo rozsah povolený `typename` , Visual Basic vyvolá výjimku.

`typename`Libovolný výraz, který je platný v rámci `As` klauzule v `Dim` příkazu, to znamená název libovolného datového typu, objektu, struktury, třídy nebo rozhraní.

## <a name="remarks"></a>Poznámky

> [!TIP]
> K provedení převodu typu můžete použít taky následující funkce:
>
> - Funkce pro převod typů `CByte` , například, `CDbl` a `CInt` , které provádějí převod na konkrétní datový typ. Další informace najdete v tématu [funkce pro převod typů](type-conversion-functions.md).
> - [Operátor DirectCast](../operators/directcast-operator.md) nebo [operátor TryCast](../operators/trycast-operator.md) Tyto operátory vyžadují, aby jeden typ dědil z nebo implementoval jiný typ. Můžou poskytovat poněkud lepší výkon než `CType` při převodu do a z `Object` datového typu.

`CType`je zkompilována jako vložená, což znamená, že kód převodu je součástí kódu, který vyhodnocuje výraz. V některých případech kód běží rychleji, protože pro provedení převodu nejsou volány žádné procedury.

Pokud není definován žádný převod z `expression` na `typename` (například z `Integer` na `Date` ), Visual Basic zobrazí chybovou zprávu při kompilaci.

Pokud se převod v době běhu nezdařil, je vyvolána příslušná výjimka. V případě neúspěchu zužujícího převodu <xref:System.OverflowException> je nejčastější výsledek. Pokud převod není definován, je <xref:System.InvalidCastException> vyvolána. Například k tomu může dojít, pokud `expression` je typ `Object` a jeho typ za běhu nemá konverzi na `typename` .

Pokud datový typ `expression` nebo `typename` je třída nebo struktura, kterou jste definovali, můžete definovat `CType` v této třídě nebo struktuře jako operátor převodu. To slouží `CType` jako *přetížený operátor*. Pokud to uděláte, můžete řídit chování převodu do a z vaší třídy nebo struktury, včetně výjimek, které mohou být vyvolány.

## <a name="overloading"></a>Přetížení

`CType`Operátor může být také přetížen pro třídu nebo strukturu definovanou mimo váš kód. Pokud se váš kód převede na nebo z takové třídy nebo struktury, ujistěte se, že rozumíte chování `CType` operátoru. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).

## <a name="converting-dynamic-objects"></a>Převod dynamických objektů

Převody typů dynamických objektů jsou prováděny uživatelsky definovanými dynamickými převody, které používají <xref:System.Dynamic.DynamicObject.TryConvert%2A> <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> metody nebo. Pokud pracujete s dynamickými objekty, použijte <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> metodu pro převod dynamického objektu.

## <a name="example"></a>Příklad

Následující příklad používá `CType` funkci k převodu výrazu na `Single` datový typ.

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

Další příklady naleznete v tématu [implicitní a explicitní převody](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).

## <a name="see-also"></a>Viz také

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [Funkce pro převod typů](type-conversion-functions.md)
- [Převodní funkce](conversion-functions.md)
- [Operator – příkaz](../statements/operator-statement.md)
- [Postupy: Definice operátoru převodu](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Převod typů v rozhraní .NET Framework](../../../standard/base-types/type-conversion.md)
