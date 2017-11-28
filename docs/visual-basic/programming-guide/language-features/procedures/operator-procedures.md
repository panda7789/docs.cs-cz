---
title: "Procedury operátoru (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 865695731dd591b0c48f4416814fa97edf4ea42e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="operator-procedures-visual-basic"></a>Procedury operátoru (Visual Basic)
Procedury operátora je řada [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] příkazy, které definují chování standardní operátoru (například `*`, `<>`, nebo `And`) na třídu nebo strukturu jste definovali. To se označuje taky jako *přetížení operátoru*.  
  
## <a name="when-to-define-operator-procedures"></a>Při definování procedury operátoru  
 Pokud jste definovali třídu nebo strukturu, můžou deklarovat proměnné, které chcete být typu třídy nebo struktura. V některých případech musí tuto proměnnou součástí operace v rámci výrazu. Chcete-li to provést, musí být operand operátoru.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Definuje operátory jenom na jeho základní datové typy. Můžete definovat chování operátor Pokud jeden nebo oba operandy jsou typu třídu nebo strukturu.  
  
 Další informace najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="types-of-operator-procedure"></a>Typy procedury operátora  
 Procedury operátora může být jedna z následujících typů:  
  
-   Definice unární operátor kde argument je typu třídu nebo strukturu.  
  
-   Definice binární operátor kde alespoň jeden z argumentů je typu třídu nebo strukturu.  
  
-   Definice operátora převodu kde argument je typu třídu nebo strukturu.  
  
-   Definice operátora převodu, který vrátí typ třídu nebo strukturu.  
  
 Operátory převodu jsou vždy Unární a vždy používat `CType` jako operátor definujete.  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 Syntaxe deklarace procedury operátora vypadá takto:  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol* `(` *operand1*`[,`*operand2* `]) As` *datový typ*   
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Můžete použít `Widening` nebo `Narrowing` – klíčové slovo pouze na operátor převodu typu. Symbol operátoru je vždy [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) pro operátor převodu typu.  
  
 Deklarování dva operandy k definování binární operátor a deklarovat jeden operand k definování unární operátor, včetně operátor převodu typu. Je nutné deklarovat všechny operandy `ByVal`.  
  
 Deklarovat stejným způsobem jako deklarovat parametry pro každý operand [Sub – procedury](./sub-procedures.md).  
  
### <a name="data-type"></a>Datový typ  
 Vzhledem k tomu, že definujete operátor na třídu nebo strukturu, které jste definovali, alespoň jeden z operandy musí být data typu třídy nebo struktura. Pro operátor převodu typu musí být buď operand nebo návratový typ datového typu třídy nebo struktura.  
  
 Další podrobnosti najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="calling-syntax"></a>Syntaxe volání  
 Vyvolání procedury operátora implicitně pomocí symbol operátoru ve výrazu. Můžete zadat operandy stejným způsobem můžete udělat pro předdefinované operátory.  
  
 Syntaxe implicitní volání procedury operátora vypadá takto:  
  
 `Dim testStruct As`  *%{structurename/*  
  
 `Dim testNewStruct As`  *%{structurename/*`= testStruct`*operatorsymbol*   `10`  
  
### <a name="illustration-of-declaration-and-call"></a>Obrázek deklarace a volání  
 Následující strukturu ukládá hodnotu číslo se znaménkem 128-bit jako základních horní a nejnižší částí. Definuje, `+` operátor přidat dva `veryLong` hodnoty a generovat výsledném `veryLong` hodnotu.  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 Následující příklad ukazuje typické volání `+` operátor definované na `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 Další informace a příklady naleznete v tématu [operátor přetížení Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Sub – procedury](./sub-procedures.md)  
 [Function – procedury](./function-procedures.md)  
 [Procedury vlastností](./property-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Postupy: definice operátora](./how-to-define-an-operator.md)  
 [Postupy: definice operátora převodu](./how-to-define-a-conversion-operator.md)  
 [Postupy: volání procedury operátora](./how-to-call-an-operator-procedure.md)  
 [Postupy: použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md)
