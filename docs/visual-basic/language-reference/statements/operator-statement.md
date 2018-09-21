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
ms.openlocfilehash: 69dea99cf71bd1e091116e54e244abfca291ffdb
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46517897"
---
# <a name="operator-statement"></a>Operator – příkaz
Deklaruje symbol operátoru, operandy a kód, který definuje proceduru operátoru pro třídu nebo strukturu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Volitelné. Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `Public`  
 Požadováno. Označuje, že tento postup operátor [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup.  
  
 `Overloads`  
 Volitelné. Zobrazit [přetížení](../../../visual-basic/language-reference/modifiers/overloads.md).  
  
 `Shared`  
 Požadováno. Označuje, že je tento postup operátor [Shared](../../../visual-basic/language-reference/modifiers/shared.md) postup.  
  
 `Shadows`  
 Volitelné. Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `Widening`  
 Vyžaduje se pro operátor převodu, pokud zadáte `Narrowing`. Označuje, že tento postup operátor definuje [Widening](../../../visual-basic/language-reference/modifiers/widening.md) převodu. Na tuto stránku nápovědy naleznete v tématu "Rozšíření a zúžení převodů".  
  
 `Narrowing`  
 Vyžaduje se pro operátor převodu, pokud zadáte `Widening`. Označuje, že tento postup operátor definuje [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) převodu. Na tuto stránku nápovědy naleznete v tématu "Rozšíření a zúžení převodů".  
  
 `operatorsymbol`  
 Požadováno. Symbol nebo identifikátor operátor, který definuje této procedury operátora.  
  
 `operand1`  
 Požadováno. Název a typ jeden operand unárního operátoru (včetně operátor převodu) nebo levý operand binárního operátoru.  
  
 `operand2`  
 Vyžaduje se pro binární operátory. Název a typ pravý operand binárního operátoru.  
  
 `operand1` a `operand2` mají následující syntaxi a části:  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|Část|Popis|  
|----------|-----------------|  
|`ByVal`|Musí být nepovinné, ale mechanismus předávání [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).|  
|`operandname`|Požadováno. Název proměnné představující tento operand. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`operandtype`|Volitelné Pokud `Option Strict` je `On`. Datový typ tohoto operandu.|  
  
 `type`  
 Volitelné Pokud `Option Strict` je `On`. Vrací datový typ hodnoty procedury operátora.  
  
 `statements`  
 Volitelné. Blok příkazů, které spouští procedury operátora.  
  
 `returnvalue`  
 Požadováno. Hodnota, která procedury operátora vrátí volajícímu kódu.  
  
 `End``Operator`  
 Požadováno. Ukončí definici této procedury operátora.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Operator` pouze ve třídě nebo struktuře. To znamená, že *kontext deklarace* operátor nesmí být zdrojový soubor, obor názvů, modulu, rozhraní, procedura nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Musí být všechny operátory `Public Shared`. Nelze zadat `ByRef`, `Optional`, nebo `ParamArray` pro jeden z operandů.  
  
 Symbol operátoru nebo identifikátor nelze použít k uložení návratovou hodnotu. Je nutné použít `Return` příkaz který musíte zadat hodnotu. Libovolný počet `Return` příkazů může vyskytovat kdekoli v postupu.  
  
 Definování operátor tento způsob se nazývá *přetížení operátoru*to, jestli používáte `Overloads` – klíčové slovo. V následující tabulce jsou uvedeny operátory, které můžete definovat.  
  
|Typ|Operátory|  
|----------|---------------|  
|Unární|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|binární|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Převod (unární)|`CType`|  
  
 Všimněte si, že `=` operátor v binárním seznamu je relační operátor, operátor přiřazení.  
  
 Při definování `CType`, musíte zadat buď `Widening` nebo `Narrowing`.  
  
## <a name="matched-pairs"></a>Odpovídající páry  
 Některé operátory je nutné definovat jako odpovídající dvojice. Pokud definujete buď operátor tyto dvojice, je nutné definovat druhé také. Odpovídající páry jsou následující:  
  
-   `=` a `<>`  
  
-   `>` a `<`  
  
-   `>=` a `<=`  
  
-   `IsTrue` a `IsFalse`  
  
## <a name="data-type-restrictions"></a>Omezení typu dat  
 Každý operátor, který definujete musí zahrnovat třídy nebo struktury, ve kterém můžete definovat. To znamená, že třída nebo struktura musí být uvedena jako datový typ z následujících akcí:  
  
-   Operand unárního operátoru.  
  
-   Nejméně jeden z operandů binárního operátoru.  
  
-   Operand nebo návratového typu operátoru převodu.  
  
 Některé operátory mají další datový typ omezení, následujícím způsobem:  
  
-   Pokud definujete `IsTrue` a `IsFalse` operátory, musí oba vracejí `Boolean` typu.  
  
-   Pokud definujete `<<` a `>>` operátory, je nutné obojí zadat `Integer` zadejte `operandtype` z `operand2`.  
  
 Návratový typ nemá tak, aby odpovídaly typu jeden z operandů. Například operátor porovnání jako `=` nebo `<>` může vrátit `Boolean` i v případě, že ani jeden operand není `Boolean`.  
  
## <a name="logical-and-bitwise-operators"></a>Logické a bitové operátory  
 `And`, `Or`, `Not`, A `Xor` operátory mohou provádět logické a bitové operace v jazyce Visual Basic. Ale pokud definujete jeden z těchto operátorů v třídě nebo struktuře, můžete definovat pouze jeho bitová operace.  
  
 Nelze definovat `AndAlso` operátor přímo s `Operator` příkazu. Můžete však použít `AndAlso` Pokud jste splnili tyto podmínky:  
  
-   Jste definovali `And` na stejné typy operandů, kterou chcete použít pro `AndAlso`.  
  
-   Definice `And` vrátí hodnotu stejného typu jako třídy nebo struktury, na kterém jste ji definovali.  
  
-   Jste definovali `IsFalse` operátor v třídě nebo struktuře, na které jste definovali `And`.  
  
 Podobně můžete použít `OrElse` Pokud jste definovali `Or` u stejné operandů s návratovým typem třídy nebo struktury a jste definovali `IsTrue` v třídě nebo struktuře.  
  
## <a name="widening-and-narrowing-conversions"></a>Rozšíření a zúžení převodů  
 A *rozšiřující převod* vždy úspěšná v době běhu, zatímco *zužující převod* za běhu nemusí zdařit. Další informace najdete v tématu [Widening a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Pokud deklarujete proceduru převod bude `Widening`, váš kód procedury nesmí generovat žádné chyby. To znamená, následující:  
  
-   Platná hodnota typu musí vracet vždycky `type`.  
  
-   Je musí zpracovat všechny výjimky a další chybové stavy.  
  
-   Vrátí všechny chyby z všechny postupy, které volá, je musí zpracovat.  
  
 Pokud existuje riziko, které by se nemusela podařit proceduru převod, nebo ji může dojít k neošetřené výjimce, je třeba deklarovat bude `Narrowing`.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Operator` příkaz k definování obrysu strukturu, která zahrnuje procedury operátoru pro `And`, `Or`, `IsFalse`, a `IsTrue` operátory. `And` a `Or` každý používají dva operandy typu `abc` a návratový typ `abc`. `IsFalse` a `IsTrue` každá vzít jeden operand typu `abc` a vrátit `Boolean`. Tyto definice povolit, aby volající kód použít `And`, `AndAlso`, `Or`, a `OrElse` s operandy typu `abc`.  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Operátor IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [Operátor IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Postupy: Definice operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Postupy: Definice operátoru převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Postupy: Volání procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)  
 [Postupy: Použití třídy, která definuje operátory](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
