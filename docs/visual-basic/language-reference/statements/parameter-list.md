---
title: Seznam parametrů
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
ms.openlocfilehash: 706fc2414806db5608cce410bf4156839ec2d83e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404314"
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
Nepovinný parametr. Seznam atributů, které se vztahují na tento parametr. [Seznam atributů](attribute-list.md) musíte uzavřít do lomených závorek (" `<` " a " `>` ").

`Optional`  
Nepovinný parametr. Určuje, že tento parametr není při volání procedury vyžadován.

`ByVal`  
Nepovinný parametr. Určuje, že procedura nemůže nahradit nebo změnit přiřazení elementu proměnné odpovídající argumentu v volajícím kódu.

`ByRef`  
Nepovinný parametr. Určuje, že procedura může upravit základní prvek proměnné v volajícím kódu stejným způsobem, jako může samotný volající kód.

`ParamArray`  
Nepovinný parametr. Určuje, že poslední parametr v seznamu parametrů je volitelné pole prvků zadaného datového typu. To umožňuje volajícímu kódu předat libovolný počet argumentů postupu.

`parametername`  
Povinná hodnota. Název místní proměnné představující parametr

`parametertype`  
Požadováno v `Option Strict` případě `On` , že je. Datový typ lokální proměnné představující parametr

`defaultvalue`  
Vyžaduje se pro `Optional` parametry. Libovolný konstantní nebo konstantní výraz, který je vyhodnocen jako datový typ parametru. Pokud je typ `Object` , nebo třída, rozhraní, pole nebo struktura, může být výchozí hodnota pouze `Nothing` .

## <a name="remarks"></a>Poznámky

Parametry jsou obklopeny závorkami a odděleny čárkami. Parametr lze deklarovat s libovolným datovým typem. Pokud nezadáte `parametertype` , použije se výchozí hodnota `Object` .

Když volající kód volá proceduru, předá *argument* každému požadovanému parametru. Další informace najdete v tématu [rozdíly mezi parametry a argumenty](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).

Argument, který volající kód předává každému parametru, je ukazatel na základní prvek v volajícím kódu. Pokud je tento prvek *neproměnný* (konstanta, literál, výčet nebo výraz), není možné, aby se kód změnil. Pokud se jedná o prvek *proměnné* (deklarovaná proměnná, pole, vlastnost, prvek pole nebo prvek struktury), volající kód ho může změnit. Další informace naleznete v tématu [rozdíly mezi upravitelnými a neupravitelnými argumenty](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).

Pokud je předán prvek proměnné `ByRef` , může postup změnit také. Další informace naleznete v tématu [rozdíly mezi předáním argumentu podle hodnoty a podle reference](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).

## <a name="rules"></a>Pravidla

- **Závorky.** Pokud zadáte seznam parametrů, je nutné jej uzavřít do závorek. Pokud žádné parametry neexistují, můžete stále používat kulaté závorky ohraničující prázdný seznam. Tím se zlepší čitelnost kódu tím, že objasněte, že prvek je procedura.

- **Volitelné parametry.** Použijete-li `Optional` modifikátor u parametru, všechny následující parametry v seznamu musí být také nepovinné a deklarovány pomocí `Optional` modifikátoru.

     Každá deklarace volitelného parametru musí zadat `defaultvalue` klauzuli.

     Další informace najdete v tématu [volitelné parametry](../../programming-guide/language-features/procedures/optional-parameters.md).

- **Pole parametrů.** Je nutné zadat `ByVal` pro `ParamArray` parametr.

     `Optional` `ParamArray` Ve stejném seznamu parametrů nelze použít obojí a.

     Další informace naleznete v tématu [pole parametrů](../../programming-guide/language-features/procedures/parameter-arrays.md).

- **Mechanismus předávání.** Výchozím mechanismem pro každý argument je `ByVal` , což znamená, že procedura nemůže změnit základní prvek proměnné. Nicméně pokud je prvek odkazový typ, může procedura změnit obsah nebo členy podkladového objektu, přestože nemůže nahradit nebo změnit přiřazení samotného objektu.

- **Názvy parametrů** Pokud je datovým typem parametru pole, Sledujte `parametername` ihned závorky. Další informace o názvech parametrů naleznete v tématu [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje `Function` proceduru, která definuje dva parametry.

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Function – příkaz](function-statement.md)
- [Sub – příkaz](sub-statement.md)
- [Declare – příkaz](declare-statement.md)
- [Structure – příkaz](structure-statement.md)
- [Option Strict – příkaz](option-strict-statement.md)
- [Přehled atributů](../../programming-guide/concepts/attributes/index.md)
- [Postupy: Přerušení a kombinování příkazů v kódu](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
