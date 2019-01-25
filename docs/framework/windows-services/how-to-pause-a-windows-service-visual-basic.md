---
title: 'Postupy: Pozastavení služby Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
author: ghogen
ms.openlocfilehash: 8d378aba5ad09a38d24359fda8b50de072c58035
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612720"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="b56de-102">Postupy: Pozastavení služby Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b56de-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="b56de-103">V tomto příkladu <xref:System.ServiceProcess.ServiceController> součásti pozastavit služba správy služby IIS v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="b56de-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b56de-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b56de-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="b56de-105">Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="b56de-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="b56de-106">V dialogu pro výběr fragmentu kódu je umístěn v **operačního systému Windows > služby Windows**.</span><span class="sxs-lookup"><span data-stu-id="b56de-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="b56de-107">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="b56de-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b56de-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b56de-108">Compiling the Code</span></span>  
 <span data-ttu-id="b56de-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b56de-109">This example requires:</span></span>  
  
-   <span data-ttu-id="b56de-110">Odkaz na projekt do System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="b56de-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="b56de-111">Přístup k členům <xref:System.ServiceProcess> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b56de-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="b56de-112">Přidat `Imports` příkazu, pokud jste nejsou kvalifikaci plně názvy členů ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="b56de-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="b56de-113">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="b56de-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b56de-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="b56de-114">Robust Programming</span></span>  
 <span data-ttu-id="b56de-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Vlastnost <xref:System.ServiceProcess.ServiceController> místního počítače ve výchozím nastavení je třída.</span><span class="sxs-lookup"><span data-stu-id="b56de-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="b56de-116">Chcete-li odkazovat služeb Windows na jiný počítač, změňte <xref:System.ServiceProcess.ServiceController.MachineName%2A> nastavte název tohoto počítače.</span><span class="sxs-lookup"><span data-stu-id="b56de-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="b56de-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="b56de-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b56de-118">Službu nelze pozastavit.</span><span class="sxs-lookup"><span data-stu-id="b56de-118">The service cannot be paused.</span></span> <span data-ttu-id="b56de-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="b56de-119">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="b56de-120">Došlo k chybě při přístupu k systému rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b56de-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="b56de-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="b56de-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b56de-122">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b56de-122">.NET Framework Security</span></span>  
 <span data-ttu-id="b56de-123">Řízení služeb v počítači může být omezena pomocí <xref:System.ServiceProcess.ServiceControllerPermissionAccess> nastavení oprávnění ve <xref:System.ServiceProcess.ServiceControllerPermission>.</span><span class="sxs-lookup"><span data-stu-id="b56de-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="b56de-124">Přístup k informacím o služby může být omezena pomocí <xref:System.Security.Permissions.PermissionState> nastavení oprávnění ve <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="b56de-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b56de-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b56de-125">See also</span></span>
- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="b56de-126">Postupy: Pokračování služby Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b56de-126">How to: Continue a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
