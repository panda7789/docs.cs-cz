---
title: Sub – procedury
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
ms.openlocfilehash: 7848dc07d6462622685cdbea92202585f4d5d2c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352524"
---
# <a name="sub-procedures-visual-basic"></a>Sub – procedury (Visual Basic)
Procedura `Sub` je série Visual Basic příkazů, které jsou uzavřeny příkazy `Sub` a `End Sub`. Procedura `Sub` provede úlohu a vrátí řízení volajícímu kódu, ale nevrátí hodnotu volajícímu kódu.  
  
 Pokaždé, když je procedura volána, její příkazy jsou spouštěny, počínaje prvním spustitelným příkazem po příkazu `Sub` a končící prvním `End Sub`, `Exit Sub`nebo `Return`m příkazem.  
  
 Můžete definovat `Sub` proceduru v modulech, třídách a strukturách. Ve výchozím nastavení je `Public`, což znamená, že ho můžete volat odkudkoli v aplikaci, která má přístup k modulu, třídě nebo struktuře, ve které jste ji definovali. Termín, *Metoda*, popisuje `Sub` nebo `Function` postup, který je k dispozici mimo jeho definující modul, třídu nebo strukturu. Další informace najdete v tématu [postupy](./index.md).  
  
 `Sub` procedura může přebírat argumenty, jako jsou konstanty, proměnné nebo výrazy, které jsou předány volajícím kódem.  
  
## <a name="declaration-syntax"></a>Syntaxe deklarace  
 Syntaxe pro deklaraci `Sub` postup je následující:  
  
 *modifikátory* *`[` `] Sub``[(`* *parameterlist* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers` může určovat úroveň přístupu a informace o přetížení, přepsání, sdílení a stínování. Další informace naleznete v tématu [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Deklarace parametru  
 Každý parametr procedury deklarujete podobně, jak deklarujete proměnnou, zadáním názvu parametru a datového typu. Můžete také zadat mechanismus předávání a to, zda je parametr volitelný, nebo pole parametrů.  
  
 Syntaxe pro každý parametr v seznamu parametrů je následující:  
  
 *datový typ*`As``[Optional] [ByVal | ByRef] [ParamArray]`*ParameterName*  
  
 Pokud je parametr volitelný, musíte také zadat výchozí hodnotu jako součást její deklarace. Syntaxe pro určení výchozí hodnoty je následující:  
  
 `Optional [ByVal | ByRef]`*parametername*`As`*DataType*`=`*DefaultValue*  
  
### <a name="parameters-as-local-variables"></a>Parametry jako lokální proměnné  
 Při předání řízení proceduře je každý parametr považován za místní proměnnou. To znamená, že jeho životnost je stejná jako procedura a jeho rozsah je celý postup.  
  
## <a name="calling-syntax"></a>Syntaxe volání  
 Vyvoláte `Sub` proceduru explicitně pomocí příkazu samostatného volání. Nemůžete ji volat pomocí jejího názvu ve výrazu. Je nutné zadat hodnoty pro všechny argumenty, které nejsou volitelné, a je třeba uzavřít seznam argumentů v závorkách. Pokud nejsou zadány žádné argumenty, můžete volitelně vynechat závorky. Použití klíčového slova `Call` je volitelné, ale nedoporučuje se.  
  
 Syntaxe pro volání `Sub` postup je následující:  
  
 `[Call]` *`[(`* *ArgumentList* `)]`  
  
 Metodu `Sub` můžete volat vně třídy, která ji definuje. Nejdříve je nutné použít klíčové slovo `New` pro vytvoření instance třídy nebo volání metody, která vrací instanci třídy. Další informace najdete v tématu [New operator](../../../../visual-basic/language-reference/operators/new-operator.md). Pak můžete použít následující syntaxi pro volání metody `Sub` objektu instance:  
  
 *Objekt*. *methodname*`[(`*ArgumentList*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustrace deklarace a volání  
 Následující postup `Sub` informuje operátora počítače, který úkol aplikace provede, a také zobrazí časové razítko. Namísto duplikování tohoto kódu na začátku každé úlohy aplikace volá pouze `tellOperator` z různých umístění. Každé volání předá řetězec v argumentu `task`, který identifikuje spuštěnou úlohu.  
  
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
- [Postupy: volání obslužné rutiny události v Visual Basic](./how-to-call-an-event-handler.md)
