---
title: 'Postupy: Pokračování služby systému Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
author: ghogen
ms.openlocfilehash: 255dccfb74eced63ffbeff7ef567083a504cc6da
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47401287"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="e6fb8-102">Postupy: Pokračování služby systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6fb8-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="e6fb8-103">V tomto příkladu <xref:System.ServiceProcess.ServiceController> komponenty pokračujte služba správy služby IIS v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6fb8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6fb8-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="e6fb8-105">Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="e6fb8-106">V dialogu pro výběr fragmentu kódu je umístěn v **operačního systému Windows > služby Windows**.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="e6fb8-107">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="e6fb8-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e6fb8-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e6fb8-108">Compiling the Code</span></span>  
 <span data-ttu-id="e6fb8-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e6fb8-109">This example requires:</span></span>  
  
-   <span data-ttu-id="e6fb8-110">Odkaz na projekt do System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="e6fb8-111">Přístup k členům <xref:System.ServiceProcess> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="e6fb8-112">Přidat `Imports` příkazu, pokud jste nejsou kvalifikaci plně názvy členů ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="e6fb8-113">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="e6fb8-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e6fb8-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="e6fb8-114">Robust Programming</span></span>  
 <span data-ttu-id="e6fb8-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Vlastnost <xref:System.ServiceProcess.ServiceController> místního počítače ve výchozím nastavení je třída.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="e6fb8-116">Chcete-li odkazovat služeb Windows na jiný počítač, změňte <xref:System.ServiceProcess.ServiceController.MachineName%2A> nastavte název tohoto počítače.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="e6fb8-117">Nelze volat <xref:System.ServiceProcess.ServiceController.Continue%2A> metodu na služby, dokud je stav služby řadiče <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="e6fb8-118">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="e6fb8-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e6fb8-119">Službu nelze obnovit.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-119">The service cannot be resumed.</span></span> <span data-ttu-id="e6fb8-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="e6fb8-120">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="e6fb8-121">Došlo k chybě při přístupu k systému rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="e6fb8-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="e6fb8-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e6fb8-123">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e6fb8-123">.NET Framework Security</span></span>  
 <span data-ttu-id="e6fb8-124">Řízení služeb v počítači může být omezena pomocí <xref:System.ServiceProcess.ServiceControllerPermissionAccess> nastavení oprávnění ve výčtu <xref:System.ServiceProcess.ServiceControllerPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="e6fb8-125">Přístup k informacím o služby může být omezena pomocí <xref:System.Security.Permissions.PermissionState> nastavení oprávnění ve výčtu <xref:System.Security.Permissions.SecurityPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="e6fb8-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6fb8-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6fb8-126">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [<span data-ttu-id="e6fb8-127">Postupy: Pozastavení služby systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6fb8-127">How to: Pause a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
