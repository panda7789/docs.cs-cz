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
ms.openlocfilehash: 4ecb0b4a8fc154a179bc5d9d74ce9821cf4fea75
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56982164"
---
# <a name="parameter-list-visual-basic"></a>Seznam parametrů (Visual Basic)
Určuje parametry, které procedura očekává, že když je volána. Více parametrů jsou odděleny čárkami. Následuje syntaxe pro jeden parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a>Součásti  
 `attributelist`  
 Volitelné. Seznam atributů, které platí pro tento parametr. Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").  
  
 `Optional`  
 Volitelné. Určuje, že tento parametr není povinný, při volání této procedury.  
  
 `ByVal`  
 Volitelné. Určuje, že proces nelze nahradit nebo změna přiřazení proměnné element základní odpovídající argumentu ve volajícím kódu.  
  
 `ByRef`  
 Volitelné. Určuje, že postupem můžete upravit základní prvek proměnné ve volajícím kódu stejným způsobem, který může volající kód samotné.  
  
 `ParamArray`  
 Volitelné. Určuje, že poslední parametr v seznamu parametrů je volitelné pole prvků zadaného datového typu. To umožňuje předat libovolný počet argumentů, které procedura volající kód.  
  
 `parametername`  
 Povinný parametr. Název místní proměnnou představující parametr.  
  
 `parametertype`  
 Požadováno pokud `Option Strict` je `On`. Typ dat místní proměnnou představující parametr.  
  
 `defaultvalue`  
 Vyžaduje se pro `Optional` parametry. Libovolný konstantní nebo konstantní výraz, který se vyhodnotí na datový typ parametru. Pokud je typ `Object`, nebo třídy, rozhraní, pole nebo struktura, výchozí hodnota může být pouze `Nothing`.  
  
## <a name="remarks"></a>Poznámky  
 Parametry jsou uzavřen v závorkách a odděleny čárkami. Parametr mohou být deklarovány pomocí libovolného datového typu. Pokud nezadáte `parametertype`, použije se výchozí `Object`.  
  
 Když volající kód volá proces, předá *argument* pro každý povinný parametr. Další informace najdete v tématu [rozdíly mezi parametry a argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).  
  
 Argument, který volající kód předá ke každému parametru je ukazatel na základní element ve volajícím kódu. Pokud je tento prvek *nonvariable* (konstanta, literal, výčtu nebo výraz), není možné pro jakýkoli kód ho změnit. Pokud se jedná *proměnnou* – element (deklarované proměnné, pole, vlastnost, prvku pole nebo element struktury), volající kód může změnit. Další informace najdete v tématu [rozdíly mezi upravitelnými a Neupravitelnými argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).  
  
 Pokud je předán element proměnné `ByRef`, postup lze také změnit. Další informace najdete v tématu [rozdíly mezi předáním argumentu podle hodnoty a podle Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="rules"></a>pravidla  
  
-   **Závorky.** Pokud zadáte seznam parametrů, je nutné uzavřít do závorek. Pokud neexistují žádné parametry, můžete stále použít závorky uzavírající prázdný seznam. To zlepšuje čitelnost kódu bylo zcela zřejmé, že elementu je procedura.  
  
-   **Volitelné parametry.** Pokud používáte `Optional` modifikátor parametru, všechny následné parametry v seznamu musí být také volitelný a deklarovaná příkazem using `Optional` modifikátor.  
  
     Každý volitelný parametr prohlášení musí zadat `defaultvalue` klauzuli.  
  
     Další informace najdete v tématu [volitelné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).  
  
-   **Pole parametrů.** Je nutné zadat `ByVal` pro `ParamArray` parametru.  
  
     Nelze použít obě `Optional` a `ParamArray` ve stejném seznamu parametrů.  
  
     Další informace najdete v tématu [pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
-   **Předávání mechanismus.** Výchozí mechanismus pro každý argument je `ByVal`, což znamená, že proces nelze změnit základní prvek proměnné. Ale pokud elementu je typem odkazu, postup můžete upravit obsah nebo členy základní objekt, i když ho nelze nahradit nebo změna přiřazení samotného objektu.  
  
-   **Názvy parametrů.** Pokud parametr datový typ je pole, postupujte podle `parametername` okamžitě v závorkách. Další informace o názvy parametrů najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
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
- [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Postupy: Přerušení a kombinování příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
