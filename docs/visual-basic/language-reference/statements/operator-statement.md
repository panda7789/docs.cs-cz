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
ms.openlocfilehash: cb7fe7929e4b6e61ca3b39be5615e09182f2fe0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="operator-statement"></a>Operator – příkaz
Deklaruje symbol operátoru, operandy a kód, který definovat procedury operátora na třídu nebo strukturu.  
  
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
 Volitelné. V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `Public`  
 Požadováno. Určuje, zda má tento postup operátor [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup.  
  
 `Overloads`  
 Volitelné. V tématu [přetížení](../../../visual-basic/language-reference/modifiers/overloads.md).  
  
 `Shared`  
 Požadováno. Označuje, že je tento postup operátor [sdílené](../../../visual-basic/language-reference/modifiers/shared.md) postupu.  
  
 `Shadows`  
 Volitelné. V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `Widening`  
 Pokud nezadáte požadované pro převod operátor `Narrowing`. Označuje, že tento postup operátor definuje [Widening](../../../visual-basic/language-reference/modifiers/widening.md) převod. Na této stránce nápovědy najdete v části "Rozšíření a zúžení převodů".  
  
 `Narrowing`  
 Pokud nezadáte požadované pro převod operátor `Widening`. Označuje, že tento postup operátor definuje [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) převod. Na této stránce nápovědy najdete v části "Rozšíření a zúžení převodů".  
  
 `operatorsymbol`  
 Požadováno. Symbol nebo identifikátor operátor, který definuje tento postup operátor.  
  
 `operand1`  
 Požadováno. Název a typ jeden operand unárního operátoru (včetně operátora převodu) nebo levý operand binárního operátoru.  
  
 `operand2`  
 Vyžaduje se pro binární operátory. Název a typ pravý operand binárního operátoru.  
  
 `operand1` a `operand2` mají následující syntaxe a částí:  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|Část|Popis|  
|----------|-----------------|  
|`ByVal`|Volitelné, ale mechanismus předávání musí být [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).|  
|`operandname`|Požadováno. Název proměnné představující tento operand. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`operandtype`|Volitelné Pokud `Option Strict` je `On`. Datový typ tohoto operandu.|  
  
 `type`  
 Volitelné Pokud `Option Strict` je `On`. Vrací datový typ hodnoty procedury operátora.  
  
 `statements`  
 Volitelné. Blok příkazů, které spouští procedury operátora.  
  
 `returnvalue`  
 Požadováno. Hodnota, která vrátí kód volání procedury operátora.  
  
 `End``Operator`  
 Požadováno. Ukončí definici tohoto postupu operátor.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `Operator` pouze ve třídě nebo struktuře. To znamená *deklarace kontextu* pro operátor nemůže být zdrojový soubor, obor názvů, modul, rozhraní, postup nebo bloku. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Musí být všechny operátory `Public Shared`. Nelze zadat `ByRef`, `Optional`, nebo `ParamArray` pro buď operand.  
  
 Symbol operátoru nebo identifikátor nelze použít pro uložení návratovou hodnotu. Je nutné použít `Return` prohlášení a je třeba zadat hodnotu. Libovolný počet `Return` příkazy může vyskytovat kdekoli v postupu.  
  
 Definování operátor tímto způsobem se nazývá *přetížení operátoru*, jestli používáte `Overloads` – klíčové slovo. Následující tabulka uvádí operátory, které můžete definovat.  
  
|Typ|Operátory|  
|----------|---------------|  
|Unární|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|binární|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Převod (unární)|`CType`|  
  
 Všimněte si, že `=` operátor v seznamu binární je relační operátor, operátor přiřazení.  
  
 Když definujete `CType`, je nutné zadat buď `Widening` nebo `Narrowing`.  
  
## <a name="matched-pairs"></a>Odpovídající páry  
 Je třeba definovat určité operátory jako odpovídající páry. Pokud definujete buď operátor takové pár, je nutné zadat dalších také. Odpovídající páry jsou následující:  
  
-   `=` A `<>`  
  
-   `>` A `<`  
  
-   `>=` A `<=`  
  
-   `IsTrue` A `IsFalse`  
  
## <a name="data-type-restrictions"></a>Omezení typu dat  
 Každý operátor, který definujete musí zahrnovat třídu nebo strukturu, ve kterém můžete definovat. To znamená, že třídu nebo strukturu musí zobrazit jako datový typ následující:  
  
-   Operand unárního operátoru.  
  
-   Alespoň jeden z operandy binárního operátoru.  
  
-   Operand nebo návratový typ operátora převodu.  
  
 Některé operátory mají další datový typ omezení, následujícím způsobem:  
  
-   Pokud definujete `IsTrue` a `IsFalse` operátory, musí oba vracejí `Boolean` typu.  
  
-   Pokud definujete `<<` a `>>` operátory, musí oba zadat `Integer` zadejte `operandtype` z `operand2`.  
  
 Návratový typ tak, aby odpovídaly typu buď operand nemá. Například operátor porovnání jako `=` nebo `<>` může vrátit `Boolean` i v případě, že je ani operand `Boolean`.  
  
## <a name="logical-and-bitwise-operators"></a>Logické a bitové operátory  
 `And`, `Or`, `Not`, A `Xor` operátory mohou provádět logickou nebo bitové operace v jazyce Visual Basic. Ale pokud definujete jeden z těchto operátorů na třídu nebo strukturu, můžete definovat pouze jeho bitové operace.  
  
 Nelze definovat `AndAlso` operátor přímo s `Operator` příkaz. Můžete však použít `AndAlso` -li mít splněny následující podmínky:  
  
-   Jste definovali `And` na stejné typy operandů, kterou chcete použít pro `AndAlso`.  
  
-   Vaše definice `And` vrátí stejného typu, třídu nebo strukturu, na kterém jste ji definovali.  
  
-   Jste definovali `IsFalse` operátor na třídu nebo strukturu, na kterém jste definovali `And`.  
  
 Podobně můžete použít `OrElse` Pokud jste definovali `Or` na stejné operandy s návratovým typem třídu nebo strukturu a jste definovali `IsTrue` na třídu nebo strukturu.  
  
## <a name="widening-and-narrowing-conversions"></a>Rozšíření a zúžení převodů  
 A *rozšiřující převod* vždy úspěšné za běhu, zatímco *zužující převod* může selhat v době běhu. Další informace najdete v tématu [Widening a zužující převody](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Pokud deklarovat převod postup být `Widening`, postup kódu nesmí generovat případných selhání. To znamená následující:  
  
-   Musí vracet vždycky platnou hodnotu typu `type`.  
  
-   Je nutné zpracovat všechny možné výjimky a další chybové stavy.  
  
-   Je nutné zpracovat vrátí všechny chyby z všechny postupy, který volá.  
  
 Pokud existuje riziko, převod procedury se nemusí zdařit, nebo to může dojít k neošetřené výjimce, je potřeba deklarovat mohla být `Narrowing`.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `Operator` příkaz k definování obrys strukturu, která obsahuje operátor postupy pro `And`, `Or`, `IsFalse`, a `IsTrue` operátory. `And` a `Or` každý trvat dva operandy typu `abc` a návratový typ `abc`. `IsFalse` a `IsTrue` každý trvat jednu operand typu `abc` a vrátí `Boolean`. Tyto definice povolit volací kód, který použije `And`, `AndAlso`, `Or`, a `OrElse` s operandy typu `abc`.  
  
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
