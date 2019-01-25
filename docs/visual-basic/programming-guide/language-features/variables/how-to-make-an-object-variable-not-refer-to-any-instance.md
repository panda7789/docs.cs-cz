---
title: 'Postupy: Objekt nastavení proměnné, aby neodkazovala na žádnou instanci (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 1199fa4e126c3d15e56a6c895aecf6afcae17f0b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678509"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Postupy: Objekt nastavení proměnné, aby neodkazovala na žádnou instanci (Visual Basic)
Proměnné objektu z libovolné instance objektu můžete zrušit nastavením na [nic](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Zrušit přiřazení proměnné objektu z libovolné instance objektu  
  
-   Nastavte proměnnou na `Nothing` v příkazu přiřazení.  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud váš kód se pokusí o přístup ke členu objektu proměnné, která byla nastavena na `Nothing`, <xref:System.NullReferenceException> vyvolá. Pokud nastavíte proměnné objektu na `Nothing` často, nebo pokud je to možné, proměnná není inicializovaná, je vhodné k uzavření přístupu členů v `Try...Catch...Finally` bloku.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud používáte proměnné objektu pro objekty, které obsahují důvěrné nebo citlivé údaje, můžete nastavit proměnnou `Nothing` při nezabýváte aktivně se jeden z těchto objektů. To snižuje riziko škodlivý kód, získání přístupu k datům.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.NullReferenceException>
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Přiřazení objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Příkaz Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Řešení potíží s výjimkami: System.NullReferenceException](https://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
