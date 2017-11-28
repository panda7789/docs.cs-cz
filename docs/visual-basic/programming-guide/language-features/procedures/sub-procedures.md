---
title: "Sub – procedury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e20e0dd5ff9e2b931e5792bebb3144930826f89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sub-procedures-visual-basic"></a>Sub – procedury (Visual Basic)
A `Sub` postup je řadu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ohraničená příkazy `Sub` a `End Sub` příkazy. `Sub` Postup provede úlohu a vrátí ovládací prvek pro volací kód, ale nevrací hodnotu volání kódu.  
  
 Při každém volání procedury, jeho příkazy jsou spouštěny, počínaje prvním příkazem spustitelný soubor po `Sub` prohlášení a ukončuje se první `End Sub`, `Exit Sub`, nebo `Return` byl zjištěn příkaz.  
  
 Můžete definovat `Sub` postup v moduly, třídy a struktury. Ve výchozím nastavení, je `Public`, což znamená, že ji volat z libovolného místa ve vaší aplikaci, která má přístup k modulu, třídu nebo strukturu, ve kterém jste ji definovali. Termín, *metoda*, popisuje `Sub` nebo `Function` procedury, která je k němu přistupovat z mimo jeho definování modulu, třídu nebo strukturu. Další informace najdete v tématu [postupy](./index.md).  
  
 A `Sub` postup může trvat argumenty, jako jsou konstanty, proměnné nebo výrazy, které jsou k němu předaná volající kód.  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 Syntaxe deklarace `Sub` postup je následující:  
  
 `[`*modifikátory* `] Sub` *subname* `[(` *parameterlist*  `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers` Můžete zadat úroveň přístupu a informace o přetížení, přepsání, sdílení a stínový provoz. Další informace najdete v tématu [Sub – příkaz](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Deklarace parametru  
 Je deklarovat každý parametr postup podobně a jak je deklarovat proměnnou, zadat název a datový typ parametru. Můžete také určit mechanismus předávání a zda se jedná o volitelný parametr nebo pole parametrů.  
  
 Syntaxe pro každý parametr v seznamu parametrů je následující:  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *Název parametru*`As`*datový typ*   
  
 Pokud se jedná o volitelný parametr, musíte také zadat výchozí hodnotu v rámci jeho deklaraci. Syntaxe pro určení výchozí hodnota je následující:  
  
 `Optional [ByVal | ByRef]`  *Název parametru*`As`*datový typ*`=`*defaultvalue*   
  
### <a name="parameters-as-local-variables"></a>Parametry jako lokální proměnné  
 Pokud ovládací prvek předává do procesu, každý parametr je považovat za místní proměnné. To znamená, že jeho životnost je stejný jako postup, a její obor je celý postup.  
  
## <a name="calling-syntax"></a>Syntaxe volání  
 Vyvolání `Sub` postup explicitně příkazem samostatné volání. Ji nelze volat pomocí jeho názvu ve výrazu. Je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné a seznam argumentů je nutné uzavřít do závorek. Pokud jsou zadány žádné argumenty, můžete volitelně vynechat závorkách. Použití `Call` – klíčové slovo je volitelné, ale nedoporučuje se.  
  
 Syntaxe volání `Sub` postup je následující:  
  
 `[Call]`  *subname* `[(` *argumentlist*`)]`  
  
 Můžete volat `Sub` metody z mimo třídu, která ho definuje. Nejprve budete muset použít `New` – klíčové slovo k vytvoření instance třídy nebo volání metody, které vrací instanci třídy. Další informace najdete v tématu [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md). Pak použijte následující syntaxi pro volání `Sub` metoda instance objektu:  
  
 *Objekt*. *methodName*`[(`*argumentlist*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Obrázek deklarace a volání  
 Následující `Sub` postup informuje operátor počítače úloh, které aplikace se chystáte provést a také zobrazuje časové razítko. Místo duplikování tento kód na začátku každé úloze, aplikace právě volá `tellOperator` z různých umístění. Každé volání předá řetězec `task` argument, který identifikuje úkol spuštění.  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 Následující příklad ukazuje typické volání `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Function – procedury](./function-procedures.md)  
 [Procedury vlastností](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Sub – příkaz](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Postupy: volání procedury, která nevrátí hodnotu](./how-to-call-a-procedure-that-does-not-return-a-value.md)  
 [Postupy: volání obslužné rutiny událostí v jazyce Visual Basic](./how-to-call-an-event-handler.md)
