---
title: 'Postupy: Objekt nastavení proměnné, aby neodkazovala na žádnou instanci (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 820d4cb9d17bf467d257bfbba5f43f07228c0b4f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663558"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="6ff31-102">Postupy: Objekt nastavení proměnné, aby neodkazovala na žádnou instanci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ff31-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="6ff31-103">Proměnné objektu z libovolné instance objektu můžete zrušit nastavením na [nic](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="6ff31-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="6ff31-104">Zrušit přiřazení proměnné objektu z libovolné instance objektu</span><span class="sxs-lookup"><span data-stu-id="6ff31-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="6ff31-105">Nastavte proměnnou na `Nothing` v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="6ff31-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="6ff31-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="6ff31-106">Robust Programming</span></span>  
 <span data-ttu-id="6ff31-107">Pokud váš kód se pokusí o přístup ke členu objektu proměnné, která byla nastavena na `Nothing`, <xref:System.NullReferenceException> vyvolá.</span><span class="sxs-lookup"><span data-stu-id="6ff31-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="6ff31-108">Pokud nastavíte proměnné objektu na `Nothing` často, nebo pokud je to možné, proměnná není inicializovaná, je vhodné k uzavření přístupu členů v `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="6ff31-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6ff31-109">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6ff31-109">.NET Framework Security</span></span>  
 <span data-ttu-id="6ff31-110">Pokud používáte proměnné objektu pro objekty, které obsahují důvěrné nebo citlivé údaje, můžete nastavit proměnnou `Nothing` při nezabýváte aktivně se jeden z těchto objektů.</span><span class="sxs-lookup"><span data-stu-id="6ff31-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="6ff31-111">To snižuje riziko škodlivý kód, získání přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="6ff31-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ff31-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ff31-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="6ff31-113">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="6ff31-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="6ff31-114">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="6ff31-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="6ff31-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="6ff31-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="6ff31-116">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="6ff31-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
