---
title: Sub – procedury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: 646d7d217891dc8ea5b78f7ce30fce19fab08316
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977575"
---
# <a name="sub-procedures-visual-basic"></a>Sub – procedury (Visual Basic)
A `Sub` postup je řadu příkazů jazyka Visual Basic ohraničená `Sub` a `End Sub` příkazy. `Sub` Postupu provede úlohu a potom vrátí řízení volajícímu kódu, ale nevrací hodnotu volajícímu kódu.  
  
 Pokaždé, když volání procedury, jeho příkazy jsou spouštěny, počínaje první spustitelný příkaz po `Sub` příkazu a končí prvním `End Sub`, `Exit Sub`, nebo `Return` byl zjištěn příkaz.  
  
 Můžete definovat `Sub` postupu na portále moduly, třídy a struktury. Ve výchozím nastavení je to `Public`, což znamená, že ji volat z libovolného místa v aplikaci, která má přístup k modulu, třídy nebo struktury, ve kterém jste ji definovali. Termín, *metoda*, popisuje `Sub` nebo `Function` proceduru, která přistupuje z mimo jeho definování modulu, třídy nebo struktury. Další informace najdete v tématu [postupy](./index.md).  
  
 A `Sub` postupu můžete převzít argumenty, jako jsou konstanty, proměnné a výrazy, které jsou předávány do ní volající kód.  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 Syntaxe pro deklarování `Sub` postup je následující:  
  
 `[` *Modifikátory* `] Sub` *subname* `[(` *seznam_parametrů* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers` Můžete určit úroveň přístupu a informací o přetížení, přepsání, sdílení a stínování. Další informace najdete v tématu [příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Deklarace parametru  
 Deklarujete každý parametr procedury podobně a jak můžete deklarovat proměnnou, zadáte název a datový typ parametru. Můžete také určit mechanismu předávání a určuje, zda se jedná o volitelný parametr, nebo pole parametrů.  
  
 Syntaxe pro každý parametr v seznamu parametrů je následující:  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *Název parametru*`As`*datový typ*  
  
 Pokud se jedná o volitelný parametr, musíte také zadat výchozí hodnotu jako součást její deklarace. Syntaxe pro určení výchozí hodnota je následujícím způsobem:  
  
 `Optional [ByVal | ByRef]`  *Název parametru*`As`*datový typ*`=`*defaultvalue*  
  
### <a name="parameters-as-local-variables"></a>Parametry jako lokální proměnné  
 Při řízení se předá podle postupu, každý parametr je zpracováván jako místní proměnná. To znamená, že jeho životnost je stejný jako postup a jeho rozsah je celý postup.  
  
## <a name="calling-syntax"></a>Syntaxe volání  
 Vyvolání `Sub` postup explicitně pomocí samostatné volání příkazu. Ji nelze volat pomocí jeho názvu ve výrazu. Je nutné zadat hodnoty pro všechny argumenty, které nejsou nepovinné a je nutné uzavřít do závorek seznamu argumentů. Pokud nejsou dodány žádné argumenty, můžete volitelně vynechejte závorky. Použití `Call` – klíčové slovo je volitelné, ale nedoporučuje se.  
  
 Syntaxe pro volání `Sub` postup je následující:  
  
 `[Call]`  *subname* `[(` *seznam_argumentů* `)]`  
  
 Můžete volat `Sub` metodu z vně třídy, který ji definuje. Nejprve je nutné použít `New` – klíčové slovo k vytvoření instance třídy, nebo volat metodu, která vrací instanci třídy. Další informace najdete v tématu [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md). Potom použijte následující syntaxi pro volání `Sub` metodu na instanci objektu:  
  
 *Objekt*. *methodName*`[(`*seznam_argumentů*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Obrázek deklarace a volání  
 Následující `Sub` postup říká operátor počítače úloh, které aplikace se chystáte provést a také zobrazuje časové razítko. Namísto duplikování tento kód na začátku každé úlohy, aplikace jen volá `tellOperator` z různých umístění. Každé volání předává řetězcový v `task` argument, který identifikuje úlohy se spouští.  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 Následující příklad ukazuje typické volání `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Viz také:
- [Procedury](./index.md)
- [Procedury funkce](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Postupy: Volání procedury, která nevrací hodnotu](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [Postupy: Volání obslužné rutiny událostí v jazyce Visual Basic](./how-to-call-an-event-handler.md)
