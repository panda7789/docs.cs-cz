---
title: 'Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci (Visual Basic).'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: bf918b762261e1dd1fc4161a10203f3d0067e454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649721"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci (Visual Basic).
Můžete zrušit přidružení proměnné objektu z jakékoli instance objektu nastavením na [nic](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Pro zrušení přiřazení proměnné objektu z jakékoli instance objektu  
  
-   Nastavte proměnnou na `Nothing` v příkazu přiřazení.  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud váš kód pokusí o přístup ke členu objektová proměnná, která byla nastavena na `Nothing`, <xref:System.NullReferenceException> dojde. Pokud nastavíte proměnné objektu na `Nothing` často, nebo pokud je možné proměnnou není inicializován, je vhodné uzavřete přístupů člen v `Try...Catch...Finally` bloku.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud používáte proměnné objektu pro objekty, které obsahují důvěrné nebo citlivé údaje, můžete nastavit proměnnou `Nothing` při nejsou zabýváte aktivně s jedním z těchto objektů. Tím se snižuje riziko škodlivý kód získá přístup k datům.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.NullReferenceException>  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [Příkaz Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Řešení potíží s výjimkami: System.NullReferenceException](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
