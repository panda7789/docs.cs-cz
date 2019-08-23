---
title: 'Postupy: Pozastavení služby systému Windows (Visual Basic)'
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
ms.openlocfilehash: 20bc177ccf2646f79994553803568531233ea5c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935487"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="a0c26-102">Postupy: Pozastavení služby systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0c26-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="a0c26-103">Tento příklad používá <xref:System.ServiceProcess.ServiceController> komponentu k pozastavení služby Správce služby IIS v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="a0c26-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0c26-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0c26-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="a0c26-105">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="a0c26-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="a0c26-106">Ve výběru fragmentu kódu je umístěn v **operačním systému Windows > služby systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="a0c26-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="a0c26-107">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="a0c26-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a0c26-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a0c26-108">Compiling the Code</span></span>  
 <span data-ttu-id="a0c26-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a0c26-109">This example requires:</span></span>  
  
- <span data-ttu-id="a0c26-110">Odkaz na projekt System. ServiceProcess. dll.</span><span class="sxs-lookup"><span data-stu-id="a0c26-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="a0c26-111">Přístup ke členům <xref:System.ServiceProcess> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a0c26-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="a0c26-112">`Imports` Přidejte příkaz, pokud ve svém kódu plně nekvalifikujete názvy členů.</span><span class="sxs-lookup"><span data-stu-id="a0c26-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="a0c26-113">Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="a0c26-113">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a0c26-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="a0c26-114">Robust Programming</span></span>  
 <span data-ttu-id="a0c26-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Vlastnost<xref:System.ServiceProcess.ServiceController> třídy je ve výchozím nastavení místní počítač.</span><span class="sxs-lookup"><span data-stu-id="a0c26-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="a0c26-116">Chcete-li odkazovat na služby systému Windows na jiném <xref:System.ServiceProcess.ServiceController.MachineName%2A> počítači, změňte vlastnost na název počítače.</span><span class="sxs-lookup"><span data-stu-id="a0c26-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="a0c26-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="a0c26-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="a0c26-118">Službu nelze pozastavit.</span><span class="sxs-lookup"><span data-stu-id="a0c26-118">The service cannot be paused.</span></span> <span data-ttu-id="a0c26-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="a0c26-119">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="a0c26-120">Při přístupu k rozhraní API systému došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="a0c26-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="a0c26-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="a0c26-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a0c26-122">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a0c26-122">.NET Framework Security</span></span>  
 <span data-ttu-id="a0c26-123">Řízení služeb v počítači může být omezeno pomocí nástroje <xref:System.ServiceProcess.ServiceControllerPermissionAccess> k nastavení oprávnění <xref:System.ServiceProcess.ServiceControllerPermission>v nástroji.</span><span class="sxs-lookup"><span data-stu-id="a0c26-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="a0c26-124">Přístup k informacím o službě může být omezen použitím sady <xref:System.Security.Permissions.PermissionState> k nastavení oprávnění <xref:System.Security.Permissions.SecurityPermission>v nástroji.</span><span class="sxs-lookup"><span data-stu-id="a0c26-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c26-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0c26-125">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="a0c26-126">Postupy: Pokračování služby systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0c26-126">How to: Continue a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
