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
ms.openlocfilehash: a4a168fd1fad75f5038044d49886782f391ceb1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655129"
---
# <a name="procedures-in-visual-basic"></a>Procedury v jazyce Visual Basic
A *postup* je blok příkazů jazyka Visual Basic uzavřena příkazem deklarace (`Function`, `Sub`, `Operator`, `Get`, `Set`) a odpovídající `End` deklarace. Všechny spustitelné příkazy v jazyce Visual Basic musí být v rámci některé procedury.  
  
## <a name="calling-a-procedure"></a>Volání procedury  
 Můžete vyvolat proceduru z jiného místa v kódu. To se označuje jako *volání procedury*. Po dokončení procesu spuštění, vrátí ovládací prvek kód, který volá, která se označuje jako *volání kódu*. Volání kódu je příkaz nebo výraz v rámci příkazu, která určuje postup podle názvu a předá řízení.  
  
## <a name="returning-from-a-procedure"></a>Vrácení z procedury  
 Po dokončení spuštění procedury vrátí prvek volání kódu. K tomuto účelu můžete použít [příkaz Return](../../../../visual-basic/language-reference/statements/return-statement.md), odpovídající [ukončení příkazu](../../../../visual-basic/language-reference/statements/exit-statement.md) příkaz pro postup nebo procedury [End \<– klíčové slovo > příkaz](../../../../visual-basic/language-reference/statements/end-keyword-statement.md)příkaz. Ovládací prvek pak předá volání kódu následující bod volání procedury.  
  
-   S `Return` příkaz, řízení vrací okamžitě volání kódu. Následující příkazy `Return` příkaz se nespustí. Můžete mít více než jednu `Return` příkaz v stejným způsobem.  
  
-   S `Exit Sub` nebo `Exit Function` příkaz, řízení vrací okamžitě volání kódu. Následující příkazy `Exit` příkaz se nespustí. Můžete mít více než jednu `Exit` příkaz v stejným způsobem a můžete kombinovat `Return` a `Exit` příkazy v stejným způsobem.  
  
-   Pokud postup neobsahuje žádné `Return` nebo `Exit` příkazy, usoudí s `End Sub` nebo `End Function`, `End Get`, nebo `End Set` příkaz následující příkaz poslední postup obsahu. `End` Příkaz vrátí ovládací prvek okamžitě volající kód. Může mít jen jeden `End` příkaz v postupu.  
  
## <a name="parameters-and-arguments"></a>Parametry a argumenty  
 Ve většině případů musí fungovat na různých datových pokaždé, když ji volat procedury. Tyto informace můžete předat postupu jako součást volání procedury. Postup definuje nula nebo více *parametry*, každý z představující hodnotu se očekává, že jste jí předat. Odpovídající jednotlivé parametry v definici postup je *argument* ve volání procedury. Argument představuje hodnotu, kterou předáte odpovídajícího parametru ve volání procedury dané.  
  
## <a name="types-of-procedures"></a>Typy postupů  
 Visual Basic používá několik typů postupů:  
  
-   [Sub postupy](./sub-procedures.md) provádět různé akce, ale kód volání nevrátí hodnotu.  
  
-   Zpracování událostí postupy jsou `Sub` postupy, které jsou spouštěny v reakci na událost vyvolána akce uživatele nebo výskytu v programu.  
  
-   [Funkce postupů](./function-procedures.md) vrátit hodnotu volání kódu. Před vrácením mohou provádět další akce.

    Některé funkce napsané v C# vrátit *odkazovat návratovou hodnotu*. Volající funkce můžete upravit návratovou hodnotu a tato změna se projeví ve stavu názvem objektu. Od verze Visual Basic 2017, kód jazyka Visual Basic spotřebovat odkaz návratové hodnoty, i když se nemůže vracet hodnotu odkazem. Další informace najdete v tématu [odkaz návratové hodnoty](ref-return-values.md).
  
-   [Procedury vlastností](./property-procedures.md) vrátit a přiřadit hodnoty vlastnosti u objektů, nebo moduly.  
  
-   [Procedury operátoru](./operator-procedures.md) definují chování standardní operátoru při jedno nebo obě operandy je nově definované třídu nebo strukturu.  
  
-   [Obecné procedury v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) definovat jeden nebo více *parametry typu* kromě jejich normální parametrů, takže volající kód můžete předat konkrétní datové typy, když zavolá.  
  
## <a name="procedures-and-structured-code"></a>Postupy a strukturovaný kód  
 Každý jednotlivý řádek spustitelný kód ve vaší aplikaci musí být uvnitř některé postupu, jako například `Main`, `calculate`, nebo `Button1_Click`. Pokud velké postupy můžete rozdělit na menší části, je vaše aplikace srozumitelnější.  
  
 Postupy jsou užitečné pro provádění opakovaných nebo sdíleného úloh, například často používaných výpočty, text a řízení manipulaci a databázových operací. Postup můžete volat z mnoha různých místech v kódu, proto postupy můžete použít jako stavební bloky pro vaši aplikaci.  
  
 Strukturování kódu s postupy nabízí následující výhody:  
  
-   Postupy umožňují programy rozdělit diskrétní logické jednotky. Snadno můžete ladit, samostatné jednotky více než ladíte celý program bez postupy.  
  
-   Až budete vyvíjet postupy pro použití v jedné aplikaci, můžete je používat v jiných programů, často se žádné nebo téměř žádné změny. Tím lze zabránit zdvojení kódu.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření procedury](./how-to-create-a-procedure.md)  
 [Procedury Sub](./sub-procedures.md)  
 [Procedury funkce](./function-procedures.md)  
 [Procedury vlastnosti](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Rekurzivní procedury](./recursive-procedures.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Obecné procedury v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
