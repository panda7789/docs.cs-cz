---
title: Procedury
ms.date: 04/28/2017
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
ms.openlocfilehash: b959f4b6986bc325c97c7cbe9aeee0341832f6cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345982"
---
# <a name="procedures-in-visual-basic"></a>Procedury v jazyce Visual Basic
*Procedura* je blok Visual Basic příkazů, které jsou uzavřeny příkazem deklarace (`Function`, `Sub`, `Operator`, `Get`, `Set`) a deklarací odpovídajícího `End`. Všechny spustitelné příkazy v Visual Basic musí být v rámci určitého postupu.  
  
## <a name="calling-a-procedure"></a>Volání procedury  
 Vyvoláte proceduru z nějakého jiného místa v kódu. Tento postup se označuje jako *volání procedury*. Když je procedura dokončena, vrátí řízení kódu, který jej vyvolal, což je známo jako *volající kód*. Volající kód je příkaz nebo výraz v rámci příkazu, který určuje proceduru podle názvu a přenáší řízení na něj.  
  
## <a name="returning-from-a-procedure"></a>Vrácení z procedury  
 Procedura vrátí řízení volajícímu kódu při jeho spuštění. Chcete-li to provést, může použít [příkaz return](../../../../visual-basic/language-reference/statements/return-statement.md), příslušný příkaz [Exit příkazu](../../../../visual-basic/language-reference/statements/exit-statement.md) pro proceduru nebo příkaz [End \<klíčové slovo > příkazu](../../../../visual-basic/language-reference/statements/end-keyword-statement.md) . Řízení poté předává volajícímu kódu za bodem volání procedury.  
  
- Pomocí příkazu `Return` se ovládací prvek vrátí hned k volajícímu kódu. Příkazy, které následují po příkazu `Return`, se nespustí. Stejný postup může mít více než jeden `Return` příkaz.  
  
- Pomocí příkazu `Exit Sub` nebo `Exit Function` se ovládací prvek vrátí hned k volajícímu kódu. Příkazy, které následují po příkazu `Exit`, se nespustí. Stejný postup může mít více než jeden `Exit` příkaz a můžete kombinovat `Return` a `Exit` příkazy stejným postupem.  
  
- Pokud procedura nemá žádné `Return` ani `Exit` příkazy, dokončí s `End Sub` nebo `End Function`, `End Get`nebo `End Set`m příkazem za posledním příkazem těla procedury. Příkaz `End` vrátí řízení ihned na volající kód. V proceduře může být pouze jeden příkaz `End`.  
  
## <a name="parameters-and-arguments"></a>Parametry a argumenty  
 Ve většině případů procedura potřebuje pracovat s různými daty pokaždé, když je zavoláte. Tyto informace můžete předat proceduře jako součást volání procedury. Procedura definuje nula nebo více *parametrů*, z nichž každý představuje hodnotu, kterou očekáváte předat. Odpovídající každý parametr v definici procedury je *argumentem* volání procedury. Argument představuje hodnotu, která je předána příslušnému parametru v daném volání procedury.  
  
## <a name="types-of-procedures"></a>Typy procedur  
 Visual Basic používá několik typů procedur:  
  
- [Procedury Sub](./sub-procedures.md) provádějí akce, ale nevrací hodnotu volajícímu kódu.  
  
- Procedury pro zpracování událostí jsou `Sub` postupy, které se spouštějí v reakci na událost vyvolanou akcí uživatele nebo v programu.  
  
- [Procedury funkcí](./function-procedures.md) vracejí hodnotu volajícímu kódu. Před vrácením můžou provádět další akce.

    Některé funkce napsané C# v vrátí *návratovou hodnotu odkazu*. Volající funkce mohou změnit návratovou hodnotu a tato úprava se projeví ve stavu volaného objektu. Počínaje Visual Basic 2017 může Visual Basic kód spotřebovávat návratové hodnoty odkazů, i když nemůže vrátit hodnotu odkazem. Další informace najdete v tématu [referenční návratové hodnoty](ref-return-values.md).
  
- [Procedury vlastnosti](./property-procedures.md) vracejí a přiřazují hodnoty vlastností pro objekty nebo moduly.  
  
- [Procedury operátora](./operator-procedures.md) definují chování operátoru Standard, pokud jeden nebo oba operandy jsou nově definovanou třídou nebo strukturou.  
  
- [Obecné procedury v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) definují kromě jejich běžných parametrů jeden nebo více *parametrů typu* , takže volající kód může předat konkrétní datové typy pokaždé, když provede volání.  
  
## <a name="procedures-and-structured-code"></a>Procedury a strukturovaný kód  
 Každý řádek spustitelného kódu v aplikaci musí být v rámci některé procedury, například `Main`, `calculate`nebo `Button1_Click`. Pokud rozdělíte velké postupy na menší, vaše aplikace je čitelnější.  
  
 Procedury jsou užitečné pro provádění opakovaných nebo sdílených úkolů, jako jsou často používané výpočty, manipulace s textem a ovládacími prvky a databázové operace. Můžete zavolat proceduru z mnoha různých míst v kódu, abyste mohli používat procedury jako stavební bloky pro vaši aplikaci.  
  
 Strukturování kódu pomocí postupů vám poskytne následující výhody:  
  
- Postupy umožňují rozdělit programy do diskrétních logických jednotek. Můžete ladit samostatné jednotky snadněji, než můžete ladit celý program bez postupů.  
  
- Po vývoji postupů pro použití v jednom programu je můžete používat v jiných programech, často s malým nebo nezměněným. To pomáhá vyhnout se duplicitám kódu.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření procedury](./how-to-create-a-procedure.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkce](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Rekurzivní procedury](./recursive-procedures.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Obecné procedury v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
