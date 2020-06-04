---
title: 'Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci.'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: cce2e59cb76652937868a731ad308872d1aba2f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410448"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="f187d-102">Postupy: Nastavení proměnné objektu tak, aby neodkazovala na žádnou instanci (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f187d-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="f187d-103">Můžete zrušit přidružení objektové proměnné z libovolné instance objektu nastavením na [hodnotu Nothing](../../../language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="f187d-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="f187d-104">Zrušení přidružení objektové proměnné od libovolné instance objektu</span><span class="sxs-lookup"><span data-stu-id="f187d-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="f187d-105">Nastavte proměnnou na hodnotu `Nothing` v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="f187d-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="f187d-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f187d-106">Robust Programming</span></span>  
 <span data-ttu-id="f187d-107">Pokud se váš kód pokusí o přístup ke členu proměnné objektu, která byla nastavena na `Nothing` , dojde k <xref:System.NullReferenceException> chybě.</span><span class="sxs-lookup"><span data-stu-id="f187d-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="f187d-108">Pokud nastavíte proměnnou objektu na `Nothing` často, nebo pokud je možné, že proměnná není inicializována, je vhodné uzavřít přístup členů do `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="f187d-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f187d-109">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f187d-109">.NET Framework Security</span></span>  
 <span data-ttu-id="f187d-110">Použijete-li proměnnou objektu pro objekty, které obsahují důvěrná nebo citlivá data, můžete proměnnou nastavit na hodnotu, pokud aktivně nepracujete `Nothing` s jedním z těchto objektů.</span><span class="sxs-lookup"><span data-stu-id="f187d-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="f187d-111">To snižuje riziko, že škodlivý kód získá přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="f187d-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f187d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f187d-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="f187d-113">Proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="f187d-113">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="f187d-114">Přiřazení proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="f187d-114">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="f187d-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="f187d-115">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="f187d-116">Try...Catch....Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="f187d-116">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
