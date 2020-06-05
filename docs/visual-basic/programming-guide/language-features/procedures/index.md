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
ms.openlocfilehash: c0d9921704570c6984b203817aed8f5546b2f936
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408787"
---
# <a name="procedures-in-visual-basic"></a>Procedury v jazyce Visual Basic
*Procedura* je blok Visual Basic příkazů, které jsou uzavřeny příkazem deklarace ( `Function` ,, `Sub` , `Operator` `Get` , `Set` ) a `End` deklarací odpovídajícího. Všechny spustitelné příkazy v Visual Basic musí být v rámci určitého postupu.  
  
## <a name="calling-a-procedure"></a>Volání procedury  
 Vyvoláte proceduru z nějakého jiného místa v kódu. Tento postup se označuje jako *volání procedury*. Když je procedura dokončena, vrátí řízení kódu, který jej vyvolal, což je známo jako *volající kód*. Volající kód je příkaz nebo výraz v rámci příkazu, který určuje proceduru podle názvu a přenáší řízení na něj.  
  
## <a name="returning-from-a-procedure"></a>Vrácení z procedury  
 Procedura vrátí řízení volajícímu kódu při jeho spuštění. K tomu může použít [návratový příkaz](../../../language-reference/statements/return-statement.md), příslušný příkaz [Exit příkazu](../../../language-reference/statements/exit-statement.md) pro proceduru nebo příkaz pro [ \<keyword> ukončení](../../../language-reference/statements/end-keyword-statement.md) procedury. Řízení poté předává volajícímu kódu za bodem volání procedury.  
  
- Pomocí `Return` příkazu se ovládací prvek vrátí hned k volajícímu kódu. Příkazy, které následují po `Return` příkazu, se nespustí. Stejný postup může mít více než jeden `Return` příkaz.  
  
- Pomocí `Exit Sub` příkazu nebo se `Exit Function` ovládací prvek vrátí hned k volajícímu kódu. Příkazy, které následují po `Exit` příkazu, se nespustí. Stejným postupem můžete mít více než jeden `Exit` příkaz a můžete kombinovat `Return` a `Exit` příkazy stejným postupem.  
  
- Pokud procedura neobsahuje žádné `Return` příkazy nebo `Exit` , končí `End Sub` `End Function` příkazem or, `End Get` nebo `End Set` za posledním příkazem těla procedury. `End`Příkaz vrátí řízení okamžitě na volající kód. Procedura může obsahovat jenom jeden `End` příkaz.  
  
## <a name="parameters-and-arguments"></a>Parametry a argumenty  
 Ve většině případů procedura potřebuje pracovat s různými daty pokaždé, když je zavoláte. Tyto informace můžete předat proceduře jako součást volání procedury. Procedura definuje nula nebo více *parametrů*, z nichž každý představuje hodnotu, kterou očekáváte předat. Odpovídající každý parametr v definici procedury je *argumentem* volání procedury. Argument představuje hodnotu, která je předána příslušnému parametru v daném volání procedury.  
  
## <a name="types-of-procedures"></a>Typy procedur  
 Visual Basic používá několik typů procedur:  
  
- [Procedury Sub](./sub-procedures.md) provádějí akce, ale nevrací hodnotu volajícímu kódu.  
  
- Procedury pro zpracování událostí jsou `Sub` postupy, které se spouštějí v reakci na událost vyvolané akcí uživatele nebo v programu.  
  
- [Procedury funkcí](./function-procedures.md) vracejí hodnotu volajícímu kódu. Před vrácením můžou provádět další akce.

    Některé funkce napsané v jazyce C# vracejí *návratovou hodnotu odkazu*. Volající funkce mohou změnit návratovou hodnotu a tato úprava se projeví ve stavu volaného objektu. Počínaje Visual Basic 2017 může Visual Basic kód spotřebovávat návratové hodnoty odkazů, i když nemůže vrátit hodnotu odkazem. Další informace najdete v tématu [referenční návratové hodnoty](ref-return-values.md).
  
- [Procedury vlastnosti](./property-procedures.md) vracejí a přiřazují hodnoty vlastností pro objekty nebo moduly.  
  
- [Procedury operátora](./operator-procedures.md) definují chování operátoru Standard, pokud jeden nebo oba operandy jsou nově definovanou třídou nebo strukturou.  
  
- [Obecné procedury v Visual Basic](../data-types/generic-procedures.md) definují kromě jejich běžných parametrů jeden nebo více *parametrů typu* , takže volající kód může předat konkrétní datové typy pokaždé, když provede volání.  
  
## <a name="procedures-and-structured-code"></a>Procedury a strukturovaný kód  
 Každý řádek spustitelného kódu v aplikaci musí být uvnitř některé procedury, například `Main` , `calculate` nebo `Button1_Click` . Pokud rozdělíte velké postupy na menší, vaše aplikace je čitelnější.  
  
 Procedury jsou užitečné pro provádění opakovaných nebo sdílených úkolů, jako jsou často používané výpočty, manipulace s textem a ovládacími prvky a databázové operace. Můžete zavolat proceduru z mnoha různých míst v kódu, abyste mohli používat procedury jako stavební bloky pro vaši aplikaci.  
  
 Strukturování kódu pomocí postupů vám poskytne následující výhody:  
  
- Postupy umožňují rozdělit programy do diskrétních logických jednotek. Můžete ladit samostatné jednotky snadněji, než můžete ladit celý program bez postupů.  
  
- Po vývoji postupů pro použití v jednom programu je můžete používat v jiných programech, často s malým nebo nezměněným. To pomáhá vyhnout se duplicitám kódu.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření procedury](./how-to-create-a-procedure.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury funkcí](./function-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Rekurzivní procedury](./recursive-procedures.md)
- [Přetížení procedury](./procedure-overloading.md)
- [Obecné procedury v jazyce Visual Basic](../data-types/generic-procedures.md)
- [Objekty a třídy](../objects-and-classes/index.md)
