---
title: Procedury operátoru (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: cafc742474d6f7b46fbfb73374a59a350812a2a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639104"
---
# <a name="operator-procedures-visual-basic"></a>Procedury operátoru (Visual Basic)
Procedury operátoru je řada příkazů jazyka Visual Basic, které definují chování standardní – operátor (například `*`, `<>`, nebo `And`) na třídy nebo struktury, které jste definovali. To se také nazývá *přetížení operátoru*.  
  
## <a name="when-to-define-operator-procedures"></a>Při definování procedury operátoru  
 Po definování třídy nebo struktury můžete deklarovat proměnné typu této třídy nebo struktury. Tato proměnná je někdy potřeba zapojit do činnosti, jako součást výrazu. Chcete-li to provést, musí být operand operátoru.  
  
 Visual Basic definuje operátory pouze na jeho základní datové typy. Můžete definovat chování operátoru, pokud jeden nebo oba operandy jsou typu třídy nebo struktury.  
  
 Další informace najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="types-of-operator-procedure"></a>Typy procedury operátora  
 Procedury operátoru může být jedna z následujících typů:  
  
- Definice unárního operátoru, kde se argument typu třídy nebo struktury.  
  
- Definice binárního operátoru, kde je alespoň jeden z argumentů typu třídy nebo struktury.  
  
- Definice operátoru převodu, kde se argument typu třídy nebo struktury.  
  
- Definice operátora převodu, který vrátí typ třídy nebo struktury.  
  
 Operátory převodu jsou vždy Unární a vždy použijte `CType` jako operátor, definujete.  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 Syntaxe pro deklaraci procedury operátora vypadá takto:  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol* `(` *operand1*`[,`*operand2* `]) As` *datový typ*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Můžete použít `Widening` nebo `Narrowing` – klíčové slovo pouze v typu operátoru převodu. Symbol operátoru je vždy [funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) pro operátor převodu typu.  
  
 Deklarace dvou operandů k definování binárním operátorem a deklarujte jeden operand unárního operátoru, včetně typu operátoru převodu definovat. Všechny operandy musí být deklarován `ByVal`.  
  
 Stejným způsobem jako deklarovat parametry pro deklaraci operandem [Sub – procedury](./sub-procedures.md).  
  
### <a name="data-type"></a>Datový typ  
 Vzhledem k tomu, že definujete operátor v třídě nebo struktuře, které jste definovali, nejméně jeden z operandů musí být datový typ této třídě nebo struktuře. Pro operátor převodu typu operandu nebo návratový typ musí být datového typu třídy nebo struktury.  
  
 Další podrobnosti najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="calling-syntax"></a>Syntaxe volání  
 Vyvolání procedury operátora implicitně pomocí symbol operátoru ve výrazu. Zadáte operandy stejným způsobem jako pro předdefinované operátory.  
  
 Syntaxe pro implicitním voláním procedury operátora vypadá takto:  
  
 `Dim testStruct As`  *%{structurename/*  
  
 `Dim testNewStruct As`  *%{structurename/*`= testStruct`*operatorsymbol*  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>Obrázek deklarace a volání  
 Následující strukturu uloží hodnotu se znaménkem 128-bit jako základní části nejvyšším a nižšího řádu. Definuje `+` operátor přidejte dva `veryLong` hodnoty a generovat výsledném `veryLong` hodnotu.  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 Následující příklad ukazuje typické volání `+` operátor definován na `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkce](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Postupy: Definovat operátor](./how-to-define-an-operator.md)
- [Postupy: Definice operátora převodu](./how-to-define-a-conversion-operator.md)
- [Postupy: Volání procedury operátora](./how-to-call-an-operator-procedure.md)
- [Postupy: Použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md)
