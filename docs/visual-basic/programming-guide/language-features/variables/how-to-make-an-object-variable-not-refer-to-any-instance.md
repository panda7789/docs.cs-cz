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
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="982aa-102">Postupy: Objekt nastavení proměnné, aby neodkazovala na žádnou instanci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="982aa-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="982aa-103">Proměnné objektu z libovolné instance objektu můžete zrušit nastavením na [nic](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="982aa-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="982aa-104">Zrušit přiřazení proměnné objektu z libovolné instance objektu</span><span class="sxs-lookup"><span data-stu-id="982aa-104">To disassociate an object variable from any object instance</span></span>  
  
-   <span data-ttu-id="982aa-105">Nastavte proměnnou na `Nothing` v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="982aa-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="982aa-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="982aa-106">Robust Programming</span></span>  
 <span data-ttu-id="982aa-107">Pokud váš kód se pokusí o přístup ke členu objektu proměnné, která byla nastavena na `Nothing`, <xref:System.NullReferenceException> vyvolá.</span><span class="sxs-lookup"><span data-stu-id="982aa-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="982aa-108">Pokud nastavíte proměnné objektu na `Nothing` často, nebo pokud je to možné, proměnná není inicializovaná, je vhodné k uzavření přístupu členů v `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="982aa-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="982aa-109">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="982aa-109">.NET Framework Security</span></span>  
 <span data-ttu-id="982aa-110">Pokud používáte proměnné objektu pro objekty, které obsahují důvěrné nebo citlivé údaje, můžete nastavit proměnnou `Nothing` při nezabýváte aktivně se jeden z těchto objektů.</span><span class="sxs-lookup"><span data-stu-id="982aa-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="982aa-111">To snižuje riziko škodlivý kód, získání přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="982aa-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="982aa-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="982aa-112">See also</span></span>
- <xref:System.NullReferenceException>
- [<span data-ttu-id="982aa-113">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="982aa-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="982aa-114">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="982aa-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="982aa-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="982aa-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="982aa-116">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="982aa-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="982aa-117">Řešení potíží s výjimkami: System.NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="982aa-117">Troubleshooting Exceptions: System.NullReferenceException</span></span>](https://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
