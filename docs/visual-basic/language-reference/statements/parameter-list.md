---
title: "Seznam parametrů (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c7190b618aa98c91b826ca7c065660d3b19c31a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-list-visual-basic"></a>Seznam parametrů (Visual Basic)
Určuje parametry, které procedura očekává, že když je volána. Několik parametrů jsou oddělené čárkami. Toto je syntaxe pro jeden parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a>Součásti  
 `attributelist`  
 Volitelné. Seznam atributů, které platí pro tento parametr. Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").  
  
 `Optional`  
 Volitelné. Určuje, že tento parametr není požadovaná při volání procedury.  
  
 `ByVal`  
 Volitelné. Určuje, že postup nelze nahradit nebo přiřazení proměnných element základní odpovídající argument ve volání kódu.  
  
 `ByRef`  
 Volitelné. Určuje, že postup můžete upravit základní proměnné element v kód volání stejným způsobem, může volání samotný kód.  
  
 `ParamArray`  
 Volitelné. Určuje, že poslední parametr v seznamu parametrů je volitelné pole elementů zadaného datového typu. To umožňuje kód volání předat libovolný počet argumentů procesu.  
  
 `parametername`  
 Požadováno. Název místní proměnné reprezentující parametr.  
  
 `parametertype`  
 Požadováno pokud `Option Strict` je `On`. Datový typ místní proměnné reprezentující parametr.  
  
 `defaultvalue`  
 Vyžaduje se pro `Optional` parametry. Jakýkoli konstantní nebo konstantní výraz, jehož výsledkem je datový typ parametru. Pokud je typ `Object`, nebo třídu, rozhraní, pole nebo struktura, výchozí hodnota může být pouze `Nothing`.  
  
## <a name="remarks"></a>Poznámky  
 Parametry jsou uzavřeny v závorkách a oddělené čárkami. Parametr lze deklarovat s žádným typem data. Pokud nezadáte `parametertype`, nastaví se jako výchozí `Object`.  
  
 Volání kódu volá proceduru, předá *argument* pro každý požadovaný parametr. Další informace najdete v tématu [rozdíly mezi parametry a argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).  
  
 Argument, který volací kód předá každý parametr je ukazatel na základní elementu v kódu volání. Pokud je tento element *nonvariable* (konstanta, literál, výčet nebo výraz), není možné, aby žádný kód ho změnit. Pokud je *proměnná* – element (deklarované proměnné, pole, vlastnost, element pole nebo Struktura element), můžete ho změnit kód volání. Další informace najdete v tématu [rozdíly mezi upravitelnými a Neupravitelnými argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).  
  
 Pokud je předán element proměnné `ByRef`, postup lze také změnit. Další informace najdete v tématu [rozdíly mezi předáním argumentu podle hodnoty a podle Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="rules"></a>Pravidla  
  
-   **Závorky.** Pokud zadáte seznam parametrů, je nutné uzavřít v závorkách. Pokud neexistují žádné parametry, můžete stále závorkách obklopuje prázdný seznam. Dojde tak ke zlepšení čitelnosti kódu, které toto vyjasňují, že prvek je procedury.  
  
-   **Volitelné parametry.** Pokud použijete `Optional` modifikátor na parametr, všechny následné parametry v seznamu musí být také volitelné a deklarovat pomocí `Optional` modifikátor.  
  
     Musíte zadat všechny deklarace volitelný parametr `defaultvalue` klauzule.  
  
     Další informace najdete v tématu [volitelné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).  
  
-   **Pole parametrů.** Je nutné zadat `ByVal` pro `ParamArray` parametr.  
  
     Nemůžete použít obě `Optional` a `ParamArray` v stejný seznam parametrů.  
  
     Další informace najdete v tématu [pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
-   **Mechanismus předávání.** Výchozí mechanismus pro každý argument je `ByVal`, což znamená, postup nelze změnit základní proměnné elementu. Ale pokud element je typu odkaz, postup můžete upravit obsah nebo členy podkladového objektu, i když ho nelze nahradit nebo změna přiřazení samotného objektu.  
  
-   **Názvy parametrů.** Pokud parametr datový typ pole, postupujte podle `parametername` okamžitě v závorkách. Další informace o názvy parametrů najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `Function` procedury, která definuje dva parametry.  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Postupy: přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
