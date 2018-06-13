---
title: 'Postupy: Definice struktury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 6128addd60609bfc88a1409648fb320bc7089974
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650024"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Postupy: Definice struktury (Visual Basic)
Zahájit deklarace struktury s [Structure – příkaz](../../../../visual-basic/language-reference/statements/structure-statement.md), a její `End` `Structure` příkaz. Mezi tyto dva příkazy, musí deklarovat alespoň jeden *element*. Elementy mohou být jakéhokoli typu dat, ale alespoň jeden musí být na sdíleném proměnnou nebo sdíleném, nevlastní událostí.  
  
 Nelze inicializovat všechny elementy struktury v deklarace struktury. Když je deklarovat proměnnou být typu Struktura, přiřadit hodnoty k elementům podle k nim přistupovat pomocí proměnné.  
  
 Informace o rozdílech mezi struktury a třídy, najdete v části [struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Pro demonstrační účely Představte si situaci, kde chcete uchovávání informací o název, telefonní číslo a mzda zaměstnance. Struktury můžete k tomu do jedné proměnné.  
  
### <a name="to-declare-a-structure"></a>Chcete-li definice struktury  
  
1.  Vytvořte počáteční a koncové příkazy pro strukturu.  
  
     Můžete zadat úroveň přístupu tohoto struktura pomocí [veřejné](../../../../visual-basic/language-reference/modifiers/public.md), [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), nebo [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo, nebo můžete nechat ji ve výchozím nastavení týkají `Public`.  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  Přidáte k tělu struktury elementů.  
  
     Struktury musí mít alespoň jeden element. Musíte deklarovat každý element a zadejte úroveň přístupu pro ni. Pokud použijete [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) bez jakékoli klíčová slova, usnadnění výchozí `Public`.  
  
    ```  
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
  
     `salary` Pole v předchozím příkladu je `Private`, což znamená, že je pravděpodobně nepřístupný mimo strukturu, i z obsahující třídy. Ale `giveRaise` postup je `Public`, takže může být volána z mimo strukturu. Podobně můžete zvýšit `salaryReviewTime` událost z mimo strukturu.  
  
     Kromě proměnné `Sub` procedury a události, můžete také definovat konstanty, `Function` procedury a vlastnosti ve struktuře. Můžete určit maximálně jednu vlastnost jako *výchozí vlastnost*za předpokladu, že trvá nejméně jeden argument. Dokáže zpracovat událost se [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` postupu. Další informace najdete v tématu [postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Proměnné struktury](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [Struktury a ostatní programovací elementy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Uživatelský datový typ](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
