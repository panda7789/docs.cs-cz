---
title: Operator – příkaz
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
ms.openlocfilehash: f9e6ffe5a49715592399321ab471d73826e05d8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404392"
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
Nepovinný parametr. Viz [seznam atributů](attribute-list.md).

`Public`  
Povinná hodnota. Označuje, že tato procedura operátoru má [veřejný](../modifiers/public.md) přístup.

`Overloads`  
Nepovinný parametr. Viz [přetížení](../modifiers/overloads.md).

`Shared`  
Povinná hodnota. Označuje, že procedura tohoto operátoru je [sdílená](../modifiers/shared.md) procedura.

`Shadows`  
Nepovinný parametr. Viz [Shadows](../modifiers/shadows.md).

`Widening`  
Požadováno pro operátor převodu, pokud nezadáte `Narrowing` . Označuje, že tato procedura operátora definuje [rozšiřující](../modifiers/widening.md) převod. Viz "rozšiřující a zúžené převody" na této stránce s technickou pomocí.

`Narrowing`  
Požadováno pro operátor převodu, pokud nezadáte `Widening` . Označuje, že tato procedura operátora definuje [zužující](../modifiers/narrowing.md) převod. Viz "rozšiřující a zúžené převody" na této stránce s technickou pomocí.

`operatorsymbol`  
Povinná hodnota. Symbol nebo identifikátor operátoru, který definuje tento operátor procedury.

`operand1`  
Povinná hodnota. Název a typ jednoho operandu unárního operátoru (včetně operátoru převodu) nebo levého operandu binárního operátoru.

`operand2`  
Vyžaduje se pro binární operátory. Název a typ pravého operandu binárního operátoru.

`operand1`a `operand2` mají následující syntaxi a části:

`[ ByVal ] operandname [ As operandtype ]`

|Část|Description|
|----------|-----------------|
|`ByVal`|Volitelné, ale mechanismus předávání musí být [ByVal](../modifiers/byval.md).|
|`operandname`|Povinná hodnota. Název proměnné představující tento operand Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`operandtype`|Volitelné `Option Strict` , pokud není `On` . Datový typ tohoto operandu.|

`type`  
Volitelné `Option Strict` , pokud není `On` . Datový typ hodnoty, kterou procedura operátor vrátí

`statements`  
Nepovinný parametr. Blok příkazů, které spouští proceduru operátoru.

`returnvalue`  
Povinná hodnota. Hodnota, kterou procedura operátor vrátí na volající kód.

`End` `Operator`  
Povinná hodnota. Ukončí definici této procedury operátoru.

## <a name="remarks"></a>Poznámky

Můžete použít `Operator` pouze ve třídě nebo struktuře. To znamená, že *kontext deklarace* pro operátor nemůže být zdrojový soubor, obor názvů, modul, rozhraní, procedura nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).

Všechny operátory musí být `Public Shared` . Nemůžete zadat `ByRef` , `Optional` nebo `ParamArray` pro žádný operand.

Symbol operátoru ani identifikátor nelze použít pro uložení návratové hodnoty. Je nutné použít `Return` příkaz a musí zadat hodnotu. Libovolný počet `Return` příkazů se může objevit kdekoli v proceduře.

Definováním operátoru tímto způsobem se říká *přetížení operátoru*, bez ohledu na to, jestli používáte `Overloads` klíčové slovo. V následující tabulce jsou uvedeny operátory, které můžete definovat.

|Typ|Operátory|
|----------|---------------|
|Unární|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|
|Binární|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|
|Převod (Unární)|`CType`|

Všimněte si, že `=` operátor v binárním seznamu je operátor porovnání, nikoli operátor přiřazení.

Při definování `CType` musíte zadat buď `Widening` nebo `Narrowing` .

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

- Definujete-li `IsTrue` `IsFalse` operátory a, musí oba vracet `Boolean` typ.

- Definujete-li `<<` `>>` operátory a, musí obě určovat `Integer` typ pro `operandtype` `operand2` .

Návratový typ nemusí odpovídat typu žádného operandu. Například operátor porovnání, jako `=` je nebo, `<>` může vracet `Boolean` i v případě, že žádný operand není `Boolean` .

## <a name="logical-and-bitwise-operators"></a>Logické a bitové operátory

`And`Operátory, `Or` , `Not` a `Xor` mohou v Visual Basic provádět buď logické, nebo bitové operace. Pokud však definujete jeden z těchto operátorů pro třídu nebo strukturu, můžete definovat pouze jeho bitovou operaci.

Operátor nelze definovat `AndAlso` přímo pomocí `Operator` příkazu. Můžete však použít, `AndAlso` Pokud splňujete následující podmínky:

- Definovali jste `And` stejné typy operandů, které chcete použít pro `AndAlso` .

- Vaše definice `And` vrátí stejný typ jako třída nebo struktura, na které jste ji definovali.

- Definovali jste `IsFalse` operátor na třídě nebo struktuře, na které jste definovali `And` .

Podobně můžete použít, `OrElse` Pokud jste definovali `Or` na stejných operandech, s návratovým typem třídy nebo struktury a jste definovali `IsTrue` pro třídu nebo strukturu.

## <a name="widening-and-narrowing-conversions"></a>Rozšíření a zúžení převodů

*Rozšiřující převod* v době běhu vždy proběhne úspěšně, zatímco *zužující převod* může v době běhu selhat. Další informace najdete v tématu [rozšiřování a zúžení převodů](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

Pokud deklarujete postup převodu `Widening` , váš kód procedury nesmí generovat žádné chyby. To znamená následující:

- Vždy musí vracet platnou hodnotu typu `type` .

- Musí zpracovat všechny možné výjimky a jiné chybové stavy.

- Musí zpracovat jakékoli návratové chyby ze všech procedur, které volá.

Pokud existuje možnost, že postup převodu nemusí být úspěšný nebo že může způsobit neošetřenou výjimku, musíte deklarovat, aby byl `Narrowing` .

## <a name="example"></a>Příklad

Následující příklad kódu používá `Operator` příkaz k definování obrysu struktury, která obsahuje procedury operátoru pro `And` operátory,, a `Or` `IsFalse` `IsTrue` . `And`a `Or` každá z nich přijímá dva operandy typu `abc` a návratového typu `abc` . `IsFalse`a `IsTrue` každý z nich vezme jeden operand typu `abc` a vrátí `Boolean` . Tyto definice umožňují, aby volající kód používal `And` , `AndAlso` , `Or` a `OrElse` s operandy typu `abc` .

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a>Viz také

- [IsFalse – operátor](../operators/isfalse-operator.md)
- [IsTrue – operátor](../operators/istrue-operator.md)
- [Rozšíření](../modifiers/widening.md)
- [Narrowing](../modifiers/narrowing.md)
- [Rozšíření a zúžení převodů](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Procedury operátoru](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Postupy: Definice operátoru](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Postupy: Definice operátoru převodu](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Postupy: Volání procedury operátoru](../../programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [Postupy: Použití třídy, která definuje operátory](../../programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
