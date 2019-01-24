---
title: Procedury v jazyce Visual Basic
ms.date: 04/28/2017
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
ms.openlocfilehash: 07c6cbae11cb259ac852d33992526c855c231d4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513331"
---
# <a name="procedures-in-visual-basic"></a>Procedury v jazyce Visual Basic
A *postup* je blok příkazů jazyka Visual Basic uzavřená v příkazu deklarace (`Function`, `Sub`, `Operator`, `Get`, `Set`) a odpovídající `End` deklarace. Všechny spustitelné příkazy v jazyce Visual Basic, musí být v rámci některé procedury.  
  
## <a name="calling-a-procedure"></a>Volání procedury  
 Vyvolání procedury z jiné místo v kódu. Jedná se *TDS*. Po dokončení postupu spuštěn, vrátí ovládací prvek kódu, který vyvolá, který je označován jako *volání kódu*. Volající kód je příkaz nebo výraz v příkazu, která určuje postup podle názvu a předá řízení.  
  
## <a name="returning-from-a-procedure"></a>Vrácení z procedury  
 Po dokončení spuštění procedury vrátí řízení volajícímu kódu. K tomuto účelu můžete použít [příkaz Return](../../../../visual-basic/language-reference/statements/return-statement.md), odpovídající [příkaz Exit](../../../../visual-basic/language-reference/statements/exit-statement.md) příkaz pro proces, nebo podle postupu [End \<– klíčové slovo > příkaz](../../../../visual-basic/language-reference/statements/end-keyword-statement.md)příkazu. Ovládací prvek pak předá do volajícího kódu bodem, volání procedury.  
  
-   S `Return` prohlášení, ovládací prvek vrátí okamžitě volajícímu kódu. Následující příkazy `Return` příkaz nepoužívají. Můžete mít více než jeden `Return` příkaz ve stejné proceduře.  
  
-   Pomocí `Exit Sub` nebo `Exit Function` prohlášení, ovládací prvek vrátí okamžitě volajícímu kódu. Následující příkazy `Exit` příkaz nepoužívají. Můžete mít více než jeden `Exit` příkaz v stejným způsobem a můžete kombinovat `Return` a `Exit` příkazy ve stejné proceduře.  
  
-   Pokud procedura nemá žádné `Return` nebo `Exit` příkazy, dojde k `End Sub` nebo `End Function`, `End Get`, nebo `End Set` příkazu za poslední příkaz těla postup. `End` Příkaz okamžitě vrátí řízení volajícímu kódu. Může mít pouze jeden `End` příkaz v postupu.  
  
## <a name="parameters-and-arguments"></a>Parametry a argumenty  
 Ve většině případů je potřeba pracovat s různými daty pokaždé, když při volání procedury. Tyto informace můžete předat do postupu jako součást volání procedury. Postup definuje nula nebo více *parametry*, každý z která představuje hodnotu očekává, že jste do něj předáte. Odpovídající každý parametr v definici procedury je *argument* ve volání procedury. Argument představuje hodnotu, kterou předáte do odpovídajícího parametru ve volání daného postupu.  
  
## <a name="types-of-procedures"></a>Typy postupů  
 Jazyk Visual Basic používá několik typů postupů:  
  
-   [Sub postupy](./sub-procedures.md) provádět různé akce, ale nesmí vracet hodnotu volajícímu kódu.  
  
-   Zpracování událostí postupy jsou `Sub` postupy, které jsou spuštěny v reakci na událost zahájená uživatelem nebo výskytu v programu.  
  
-   [Funkce postupů](./function-procedures.md) vrací hodnotu volajícímu kódu. Před vrácením mohou provádět další akce.

    Některé funkce napsané v C# vrátit *odkazovat na návratovou hodnotu*. Volající funkce vrácenou hodnotu můžete změnit, a tato změna se projeví ve stavu volaný objekt. Počínaje rokem 2017 jazyka Visual Basic, Visual Basic kód může spotřebovat referenční návratové hodnoty, i když ho nemůže vracet hodnotu odkazem. Další informace najdete v tématu [referenční návratové hodnoty](ref-return-values.md).
  
-   [Procedury vlastnosti](./property-procedures.md) vrátit a přiřadit hodnoty vlastností objektů nebo moduly.  
  
-   [Procedury operátoru](./operator-procedures.md) definuje chování standardní operátor, když jeden nebo oba operandy jsou nově definované třídou nebo strukturou.  
  
-   [Obecné procedury v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) definují jednu nebo více *parametry typu* kromě běžné parametry, aby volající kód může předat konkrétní datové typy, když volání.  
  
## <a name="procedures-and-structured-code"></a>Postupy a strukturovaný kód  
 Každý jednotlivý řádek spustitelného kódu v aplikaci musí být v některých postup, například `Main`, `calculate`, nebo `Button1_Click`. Pokud rozdělíte velké postupy do menších, je vaše aplikace lépe čitelný.  
  
 Postupy jsou užitečné při provádění opakovaných nebo sdílené úloh, jako jsou často používaných výpočty, manipulaci s textem a ovládací prvek a databázových operací. Postup můžete volat z mnoha různých míst v kódu, tak postupy můžete použít jako stavební bloky pro vaši aplikaci.  
  
 Strukturování kódu pomocí procedury poskytuje následující výhody:  
  
-   Postupy umožňují rozdělit svých programů na samostatných logických jednotek. Další samostatné jednotky můžete snadno ladit než můžete ladit celého programu bez postupy.  
  
-   Poté, co při vývoji postupy pro použití v jedné aplikaci, můžete je v jiných aplikacích, často a obsahují žádné nebo téměř žádné změny. To pomáhá předejít duplikování kódu.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vytvoření procedury](./how-to-create-a-procedure.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkce](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Rekurzivní procedury](./recursive-procedures.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Obecné procedury v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
