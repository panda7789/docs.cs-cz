---
title: 'Postupy: Deklarace struktury'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: a6b70d0973e92db90e35e61b7fed2279c5b0bac3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393971"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Postupy: Definice struktury (Visual Basic)
Zahájíte deklaraci struktury pomocí [příkazu struktury](../../../language-reference/statements/structure-statement.md)a ukončíte ji `End Structure` příkazem. Mezi těmito dvěma příkazy musíte deklarovat alespoň jeden *prvek*. Prvky mohou být libovolného datového typu, ale nejméně jedna musí být buď nesdílená proměnná, nebo nesdílená, nevlastní událost.  
  
 V deklaraci struktury nelze inicializovat žádné prvky struktury. Pokud deklarujete proměnnou, která má být typu struktury, přiřazujete hodnoty k prvkům jejich přístupem přes proměnnou.  
  
 Diskuzi o rozdílech mezi strukturami a třídami naleznete v tématu [struktury a třídy](structures-and-classes.md).  
  
 Pro demonstrační účely Zvažte situaci, kdy si přejete sledovat jméno zaměstnance, telefonní linky a mzdu. Struktura vám to umožňuje v rámci jedné proměnné.  
  
### <a name="to-declare-a-structure"></a>Deklarace struktury  
  
1. Vytvořte na začátku a konci příkazy pro strukturu.  
  
     Úroveň přístupu ke struktuře můžete určit pomocí klíčového slova [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md)nebo [Private](../../../language-reference/modifiers/private.md) , nebo můžete nechat výchozí hodnotu `Public` .  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. Přidejte prvky do těla struktury.  
  
     Struktura musí mít alespoň jeden element. Musíte deklarovat každý prvek a zadat úroveň přístupu. Použijete-li [příkaz Dim](../../../language-reference/statements/dim-statement.md) bez klíčových slov, je výchozím nastavením přístupnosti `Public` .  
  
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
  
     `salary`Pole v předchozím příkladu je `Private` , což znamená, že je nepřístupný mimo strukturu, dokonce i z nadřazené třídy. `giveRaise`Postup je však `Public` , aby jej bylo možné volat mimo strukturu. Podobně lze `salaryReviewTime` událost vyvolat mimo strukturu.  
  
     Kromě proměnných, `Sub` procedur a událostí můžete také definovat konstanty, `Function` procedury a vlastnosti ve struktuře. Můžete určit maximálně jednu vlastnost jako *výchozí vlastnost*za předpokladu, že převezme aspoň jeden argument. Událost můžete zpracovat pomocí [sdílené](../../../language-reference/modifiers/shared.md) `Sub` procedury. Další informace naleznete v tématu [Postupy: deklarace a volání výchozí vlastnosti v Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Viz také

- [Datové typy](index.md)
- [Základní datové typy](elementary-data-types.md)
- [Složené datové typy](composite-data-types.md)
- [Typy hodnot a typy odkazu](value-types-and-reference-types.md)
- [Struktury](structures.md)
- [Řešení potíží s datovými typy](troubleshooting-data-types.md)
- [Proměnné struktury](structure-variables.md)
- [Struktury a ostatní programovací elementy](structures-and-other-programming-elements.md)
- [Struktury a třídy](structures-and-classes.md)
- [Uživatelský datový typ](../../../language-reference/data-types/user-defined-data-type.md)
