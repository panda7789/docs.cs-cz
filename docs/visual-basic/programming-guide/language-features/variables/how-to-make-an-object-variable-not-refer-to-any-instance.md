---
title: 'Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci (Visual Basic).'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: e647f2f891b06aa1767faac49b01df98ea31ec1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004912"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="b8980-102">Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b8980-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="b8980-103">Můžete zrušit přidružení objektové proměnné z libovolné instance objektu nastavením na [hodnotu Nothing](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="b8980-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="b8980-104">Zrušení přidružení objektové proměnné od libovolné instance objektu</span><span class="sxs-lookup"><span data-stu-id="b8980-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="b8980-105">Nastavte proměnnou na `Nothing` v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="b8980-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="b8980-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="b8980-106">Robust Programming</span></span>  
 <span data-ttu-id="b8980-107">Pokud se váš kód pokusí o přístup k členu proměnné objektu, která je nastavená na `Nothing`, dojde k <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="b8980-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="b8980-108">Pokud nastavíte proměnnou objektu na hodnotu `Nothing` často, nebo pokud je možné, že proměnná není inicializována, je vhodné uzavřít přístup členů do bloku `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="b8980-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b8980-109">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b8980-109">.NET Framework Security</span></span>  
 <span data-ttu-id="b8980-110">Použijete-li proměnnou objektu pro objekty, které obsahují důvěrné nebo citlivé údaje, můžete nastavit proměnnou na hodnotu `Nothing`, pokud se neaktivně nepracujete s jedním z těchto objektů.</span><span class="sxs-lookup"><span data-stu-id="b8980-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="b8980-111">To snižuje riziko, že škodlivý kód získá přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="b8980-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8980-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8980-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="b8980-113">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="b8980-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="b8980-114">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="b8980-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="b8980-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="b8980-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="b8980-116">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="b8980-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
