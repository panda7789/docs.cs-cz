---
title: "Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b33aef06300bf35b7138ec5b40747532a77140a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Nic](../../../../visual-basic/language-reference/nothing.md)  
 [Try... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Řešení potíží s výjimkami: System.NullReferenceException](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
