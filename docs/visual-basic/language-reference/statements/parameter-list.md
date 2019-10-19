---
title: Seznam parametrů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 0dded7fd68256b9b9de8ebe4b48073eb40696c12
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582171"
---
# <a name="parameter-list-visual-basic"></a>Seznam parametrů (Visual Basic)

Určuje parametry, které procedura očekává při volání. Více parametrů je odděleno čárkami. Následuje syntaxe pro jeden parametr.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a>Součásti

`attributelist`  
Volitelné. Seznam atributů, které se vztahují na tento parametr. [Seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) je nutné uzavřít do lomených závorek ("`<`" a "`>`").

`Optional`  
Volitelné. Určuje, že tento parametr není při volání procedury vyžadován.

`ByVal`  
Volitelné. Určuje, že procedura nemůže nahradit nebo změnit přiřazení elementu proměnné odpovídající argumentu v volajícím kódu.

`ByRef`  
Volitelné. Určuje, že procedura může upravit základní prvek proměnné v volajícím kódu stejným způsobem, jako může samotný volající kód.

`ParamArray`  
Volitelné. Určuje, že poslední parametr v seznamu parametrů je volitelné pole prvků zadaného datového typu. To umožňuje volajícímu kódu předat libovolný počet argumentů postupu.

`parametername`  
Požadováno. Název místní proměnné představující parametr

`parametertype`  
Vyžaduje se, pokud je `Option Strict` `On`. Datový typ lokální proměnné představující parametr

`defaultvalue`  
Vyžaduje se pro parametry `Optional`. Libovolný konstantní nebo konstantní výraz, který je vyhodnocen jako datový typ parametru. Pokud je typ `Object` nebo třída, rozhraní, pole nebo struktura, může být výchozí hodnota pouze `Nothing`.

## <a name="remarks"></a>Poznámky

Parametry jsou obklopeny závorkami a odděleny čárkami. Parametr lze deklarovat s libovolným datovým typem. Pokud nezadáte `parametertype`, použije se výchozí hodnota `Object`.

Když volající kód volá proceduru, předá *argument* každému požadovanému parametru. Další informace najdete v tématu [rozdíly mezi parametry a argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).

Argument, který volající kód předává každému parametru, je ukazatel na základní prvek v volajícím kódu. Pokud je tento prvek *neproměnný* (konstanta, literál, výčet nebo výraz), není možné, aby se kód změnil. Pokud se jedná o prvek *proměnné* (deklarovaná proměnná, pole, vlastnost, prvek pole nebo prvek struktury), volající kód ho může změnit. Další informace naleznete v tématu [rozdíly mezi upravitelnými a neupravitelnými argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).

Pokud je předán prvek proměnné `ByRef`, může postup změnit také. Další informace naleznete v tématu [rozdíly mezi předáním argumentu podle hodnoty a podle reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).

## <a name="rules"></a>Pravidly

- **Závorky.** Pokud zadáte seznam parametrů, je nutné jej uzavřít do závorek. Pokud žádné parametry neexistují, můžete stále používat kulaté závorky ohraničující prázdný seznam. Tím se zlepší čitelnost kódu tím, že objasněte, že prvek je procedura.

- **Volitelné parametry.** Použijete-li modifikátor `Optional` u parametru, všechny následující parametry v seznamu musí být také nepovinné a deklarovány pomocí modifikátoru `Optional`.

     Každá deklarace volitelného parametru musí poskytovat klauzuli `defaultvalue`.

     Další informace najdete v tématu [volitelné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).

- **Pole parametrů.** Pro parametr `ParamArray` je nutné zadat `ByVal`.

     Ve stejném seznamu parametrů nelze použít současně `Optional` i `ParamArray`.

     Další informace naleznete v tématu [pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).

- **Mechanismus předávání.** Výchozí mechanismus pro každý argument je `ByVal`, což znamená, že procedura nemůže změnit základní prvek proměnné. Nicméně pokud je prvek odkazový typ, může procedura změnit obsah nebo členy podkladového objektu, přestože nemůže nahradit nebo změnit přiřazení samotného objektu.

- **Názvy parametrů** Je-li datovým typem parametru pole, postupujte `parametername` bezprostředně závorkami. Další informace o názvech parametrů naleznete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje `Function` proceduru, která definuje dva parametry.

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Přehled atributů](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Postupy: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
