---
title: Operator – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: c4fae40992fa665121aff637ae427ef0cafbf547
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582386"
---
# <a name="operator-statement"></a>Operator – příkaz

Deklaruje symbol operátoru, operandy a kód, který definuje proceduru operátoru pro třídu nebo strukturu.

## <a name="syntax"></a>Syntaxe

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a>Součásti

`attrlist`  
Volitelné. Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).

`Public`  
Požadováno. Označuje, že tato procedura operátoru má [veřejný](../../../visual-basic/language-reference/modifiers/public.md) přístup.

`Overloads`  
Volitelné. Viz [přetížení](../../../visual-basic/language-reference/modifiers/overloads.md).

`Shared`  
Požadováno. Označuje, že procedura tohoto operátoru je [sdílená](../../../visual-basic/language-reference/modifiers/shared.md) procedura.

`Shadows`  
Volitelné. Viz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

`Widening`  
Požadováno pro operátor převodu, pokud nezadáte `Narrowing`. Označuje, že tato procedura operátora definuje [rozšiřující](../../../visual-basic/language-reference/modifiers/widening.md) převod. Viz "rozšiřující a zúžené převody" na této stránce s technickou pomocí.

`Narrowing`  
Požadováno pro operátor převodu, pokud nezadáte `Widening`. Označuje, že tato procedura operátora definuje [zužující](../../../visual-basic/language-reference/modifiers/narrowing.md) převod. Viz "rozšiřující a zúžené převody" na této stránce s technickou pomocí.

`operatorsymbol`  
Požadováno. Symbol nebo identifikátor operátoru, který definuje tento operátor procedury.

`operand1`  
Požadováno. Název a typ jednoho operandu unárního operátoru (včetně operátoru převodu) nebo levého operandu binárního operátoru.

`operand2`  
Vyžaduje se pro binární operátory. Název a typ pravého operandu binárního operátoru.

`operand1` a `operand2` mají následující syntaxi a části:

`[ ByVal ] operandname [ As operandtype ]`

|Částí|Popis|
|----------|-----------------|
|`ByVal`|Volitelné, ale mechanismus předávání musí být [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).|
|`operandname`|Požadováno. Název proměnné představující tento operand Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`operandtype`|Volitelné, pokud není `On` `Option Strict`. Datový typ tohoto operandu.|

`type`  
Volitelné, pokud není `On` `Option Strict`. Datový typ hodnoty, kterou procedura operátor vrátí

`statements`  
Volitelné. Blok příkazů, které spouští proceduru operátoru.

`returnvalue`  
Požadováno. Hodnota, kterou procedura operátor vrátí na volající kód.

`End``Operator`  
Požadováno. Ukončí definici této procedury operátoru.

## <a name="remarks"></a>Poznámky

@No__t_0 lze použít pouze ve třídě nebo struktuře. To znamená, že *kontext deklarace* pro operátor nemůže být zdrojový soubor, obor názvů, modul, rozhraní, procedura nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Všechny operátory musí být `Public Shared`. U obou operandů nelze zadat `ByRef`, `Optional` ani `ParamArray`.

Symbol operátoru ani identifikátor nelze použít pro uložení návratové hodnoty. Je nutné použít příkaz `Return` a musí zadat hodnotu. Libovolný počet příkazů `Return` se může objevit kdekoli v proceduře.

Definování operátoru tímto způsobem se nazývá *přetížení operátoru*, bez ohledu na to, zda použijete klíčové slovo `Overloads`. V následující tabulce jsou uvedeny operátory, které můžete definovat.

|Typ|Operátory|
|----------|---------------|
|Unární|`+`, `-`, `IsFalse`, `IsTrue` `Not`|
|binární|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, 0, 1, 2, 3, 4, 5 , 6, 7, 8 9|
|Převod (Unární)|`CType`|

Všimněte si, že operátor `=` v binárním seznamu je operátor porovnání, nikoli operátor přiřazení.

Při definování `CType` musíte zadat buď `Widening`, nebo `Narrowing`.

## <a name="matched-pairs"></a>Spárované páry

Je nutné definovat určité operátory jako spárované páry. Pokud definujete některý z operátorů takového páru, je nutné definovat i další. Spárované páry jsou následující:

- `=` a `<>`

- `>` a `<`

- `>=` a `<=`

- `IsTrue` a `IsFalse`

## <a name="data-type-restrictions"></a>Omezení datového typu

Každý operátor, který definujete, musí zahrnovat třídu nebo strukturu, na které definujete. To znamená, že třída nebo struktura se musí objevit jako datový typ následujících:

- Operand unárního operátoru.

- Nejméně jeden z operandů binárního operátoru.

- Buď operand, nebo návratový typ operátoru převodu.

 Některé operátory mají další omezení datového typu, jak je znázorněno níže:

- Pokud definujete operátory `IsTrue` a `IsFalse`, musí oba vracet typ `Boolean`.

- Pokud definujete operátory `<<` a `>>`, musí pro `operandtype` `operand2` určovat typ `Integer`.

Návratový typ nemusí odpovídat typu žádného operandu. Například operátor porovnání, například `=` nebo `<>`, může vracet `Boolean` i v případě, že není `Boolean` žádný operand.

## <a name="logical-and-bitwise-operators"></a>Logické a bitové operátory

Operátory `And`, `Or`, `Not` a `Xor` mohou v Visual Basic provádět logické nebo bitové operace. Pokud však definujete jeden z těchto operátorů pro třídu nebo strukturu, můžete definovat pouze jeho bitovou operaci.

Operátor `AndAlso` nelze definovat přímo pomocí příkazu `Operator`. Můžete však použít `AndAlso`, pokud splňujete následující podmínky:

- Definovali jste `And` pro stejné typy operandů, které chcete použít pro `AndAlso`.

- Vaše definice `And` vrací stejný typ jako třída nebo struktura, na které jste ji definovali.

- Definovali jste operátor `IsFalse` pro třídu nebo strukturu, na které jste definovali `And`.

Podobně můžete použít `OrElse`, pokud jste definovali `Or` na stejných operandech, s návratovým typem třídy nebo struktury a jste definovali `IsTrue` pro třídu nebo strukturu.

## <a name="widening-and-narrowing-conversions"></a>Rozšíření a zúžení převodů

*Rozšiřující převod* v době běhu vždy proběhne úspěšně, zatímco *zužující převod* může v době běhu selhat. Další informace najdete v tématu [rozšiřování a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

Pokud deklarujete postup převodu, který má být `Widening`, kód procedury nesmí generovat žádné chyby. To znamená následující:

- Vždy musí vracet platnou hodnotu typu `type`.

- Musí zpracovat všechny možné výjimky a jiné chybové stavy.

- Musí zpracovat jakékoli návratové chyby ze všech procedur, které volá.

Pokud existuje možnost, že postup převodu nemusí být úspěšný nebo že může způsobit neošetřenou výjimku, je nutné deklarovat, aby byla `Narrowing`.

## <a name="example"></a>Příklad

Následující příklad kódu používá příkaz `Operator` k definování obrysu struktury, která obsahuje procedury operátoru pro operátory `And`, `Or`, `IsFalse` a `IsTrue`. `And` a `Or` každý z nich přijímá dva operandy typu `abc` a návratový typ `abc`. `IsFalse` a `IsTrue` každý z nich přijímá jeden operand typu `abc` a vrací `Boolean`. Tyto definice umožňují, aby volající kód používal `And`, `AndAlso`, `Or` a `OrElse` s operandy typu `abc`.

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a>Viz také:

- [Operátor IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Operátor IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Postupy: Definice operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Postupy: Definice operátoru převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Postupy: Volání procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [Postupy: Použití třídy, která definuje operátory](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
