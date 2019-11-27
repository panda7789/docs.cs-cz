---
title: 'Postupy: Definice struktury'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 41d2d03064dea703909218de56feb863526c220b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350001"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Postupy: Definice struktury (Visual Basic)
Zahájíte deklaraci struktury pomocí [příkazu struktury](../../../../visual-basic/language-reference/statements/structure-statement.md)a ukončíte ji pomocí příkazu `End Structure`. Mezi těmito dvěma příkazy musíte deklarovat alespoň jeden *prvek*. Prvky mohou být libovolného datového typu, ale nejméně jedna musí být buď nesdílená proměnná, nebo nesdílená, nevlastní událost.  
  
 V deklaraci struktury nelze inicializovat žádné prvky struktury. Pokud deklarujete proměnnou, která má být typu struktury, přiřazujete hodnoty k prvkům jejich přístupem přes proměnnou.  
  
 Diskuzi o rozdílech mezi strukturami a třídami naleznete v tématu [struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Pro demonstrační účely Zvažte situaci, kdy si přejete sledovat jméno zaměstnance, telefonní linky a mzdu. Struktura vám to umožňuje v rámci jedné proměnné.  
  
### <a name="to-declare-a-structure"></a>Deklarace struktury  
  
1. Vytvořte na začátku a konci příkazy pro strukturu.  
  
     Úroveň přístupu ke struktuře můžete určit pomocí klíčového slova [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)nebo [Private](../../../../visual-basic/language-reference/modifiers/private.md) , nebo můžete nechat výchozí `Public`.  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. Přidejte prvky do těla struktury.  
  
     Struktura musí mít alespoň jeden element. Musíte deklarovat každý prvek a zadat úroveň přístupu. Použijete-li [příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) bez klíčových slov, je výchozí nastavení přístupnosti `Public`.  
  
    ```vb  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     Pole `salary` v předchozím příkladu je `Private`, což znamená, že je nepřístupný mimo strukturu, dokonce i z nadřazené třídy. Nicméně procedura `giveRaise` je `Public`, takže může být volána mimo strukturu. Podobně můžete vyvolat událost `salaryReviewTime` mimo strukturu.  
  
     Kromě proměnných, `Sub` procedur a událostí, můžete také definovat konstanty, `Function` procedury a vlastnosti ve struktuře. Můžete určit maximálně jednu vlastnost jako *výchozí vlastnost*za předpokladu, že převezme aspoň jeden argument. Událost můžete zpracovat pomocí [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedury. Další informace naleznete v tématu [Postupy: deklarace a volání výchozí vlastnosti v Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Proměnné struktury](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Struktury a ostatní programovací elementy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Uživatelský datový typ](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
