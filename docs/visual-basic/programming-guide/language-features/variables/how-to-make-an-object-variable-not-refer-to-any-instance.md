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
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="a0d17-102">Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a0d17-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="a0d17-103">Můžete zrušit přidružení proměnné objektu z jakékoli instance objektu nastavením na [nic](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="a0d17-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="a0d17-104">Pro zrušení přiřazení proměnné objektu z jakékoli instance objektu</span><span class="sxs-lookup"><span data-stu-id="a0d17-104">To disassociate an object variable from any object instance</span></span>  
  
-   <span data-ttu-id="a0d17-105">Nastavte proměnnou na `Nothing` v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="a0d17-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="a0d17-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="a0d17-106">Robust Programming</span></span>  
 <span data-ttu-id="a0d17-107">Pokud váš kód pokusí o přístup ke členu objektová proměnná, která byla nastavena na `Nothing`, <xref:System.NullReferenceException> dojde.</span><span class="sxs-lookup"><span data-stu-id="a0d17-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="a0d17-108">Pokud nastavíte proměnné objektu na `Nothing` často, nebo pokud je možné proměnnou není inicializován, je vhodné uzavřete přístupů člen v `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="a0d17-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a0d17-109">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a0d17-109">.NET Framework Security</span></span>  
 <span data-ttu-id="a0d17-110">Pokud používáte proměnné objektu pro objekty, které obsahují důvěrné nebo citlivé údaje, můžete nastavit proměnnou `Nothing` při nejsou zabýváte aktivně s jedním z těchto objektů.</span><span class="sxs-lookup"><span data-stu-id="a0d17-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="a0d17-111">Tím se snižuje riziko škodlivý kód získá přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="a0d17-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d17-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0d17-112">See Also</span></span>  
 <xref:System.NullReferenceException>  
 [<span data-ttu-id="a0d17-113">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="a0d17-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="a0d17-114">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="a0d17-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="a0d17-115">Nic</span><span class="sxs-lookup"><span data-stu-id="a0d17-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="a0d17-116">Try... Catch... Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="a0d17-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="a0d17-117">Řešení potíží s výjimkami: System.NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="a0d17-117">Troubleshooting Exceptions: System.NullReferenceException</span></span>](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
