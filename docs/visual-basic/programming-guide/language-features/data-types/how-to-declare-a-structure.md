---
title: 'Postupy: Definice struktury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: a52daddaa8701ccca9bd9b5b4a48535a6ffa19ed
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343555"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Postupy: Definice struktury (Visual Basic)
Začnete deklaraci struktury s [Structure – příkaz](../../../../visual-basic/language-reference/statements/structure-statement.md), a to s `End Structure` příkazu. Mezi tyto dva příkazy musí deklarovat alespoň jeden *element*. Prvků může být libovolného datového typu, ale alespoň jedna musí být nesdílené proměnné nebo nesdílených, nevlastních událostí.  
  
 Nelze inicializovat prvky struktury v deklaraci struktury. Když deklarujete proměnnou typu Struktura, přiřadit hodnoty k elementům díky přístupu prostřednictvím proměnné.  
  
 Diskuzi o rozdílech mezi struktur a tříd, naleznete v tématu [struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Pro demonstrační účely Představte si situaci, ve které chcete udržovat přehled o název, telefonní číslo a salary zaměstnance. Struktury můžete to provést v jedné proměnné.  
  
### <a name="to-declare-a-structure"></a>Chcete-li deklarovat strukturu  
  
1. Vytvořte počáteční a koncové příkazy pro strukturu.  
  
     Můžete určit úroveň přístupu pomocí struktury [veřejné](../../../../visual-basic/language-reference/modifiers/public.md), [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), nebo [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo, nebo ho můžete nechat ve výchozím nastavení `Public`.  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2. Přidáte prvky do těla struktury.  
  
     Struktura musí mít alespoň jeden element. Musíte deklarovat každý prvek a zadat úroveň přístupu pro něj. Pokud používáte [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) bez klíčová slova, přístupnost výchozí hodnota je `Public`.  
  
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
  
     `salary` Pole v předchozím příkladu je `Private`, což znamená, že není přístupná mimo strukturu, dokonce i z obsahující třídy. Ale `giveRaise` postup je `Public`, takže je možné vyvolat z mimo strukturu. Podobně můžete zvýšit `salaryReviewTime` události z mimo strukturu.  
  
     Kromě proměnných `Sub` procedury a události, můžete také definovat konstanty, `Function` postupy a vlastnosti ve struktuře. Můžete určit nejvýše jednu vlastnost jako *výchozí vlastnost*za předpokladu, že trvá nejméně jeden argument. Dokáže zpracovat událost se [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` postup. Další informace najdete v tématu [jak: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Typy hodnot a typy odkazu](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Proměnné struktury](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Struktury a ostatní programovací elementy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Struktury a třídy](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Uživatelský datový typ](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
