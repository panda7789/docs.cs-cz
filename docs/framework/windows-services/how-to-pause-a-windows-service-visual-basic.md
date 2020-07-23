---
title: 'Postupy: Pozastavení služby systému Windows (Visual Basic)'
description: Přečtěte si, jak pomocí komponenty ServiceController pozastavit službu systému Windows (například službu Správce služby IIS) na místním počítači s Visual Basic.
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
ms.openlocfilehash: 628cc2e896f7f8a289e52674b721c4aef605854c
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925563"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="2f2a7-103">Postupy: Pozastavení služby systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f2a7-103">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="2f2a7-104">Tento příklad používá <xref:System.ServiceProcess.ServiceController> komponentu k pozastavení služby Správce služby IIS v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-104">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f2a7-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f2a7-105">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="2f2a7-106">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-106">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="2f2a7-107">Ve výběru fragmentu kódu je umístěn v **operačním systému Windows > služby systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-107">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="2f2a7-108">Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="2f2a7-108">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2f2a7-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2f2a7-109">Compiling the Code</span></span>  
 <span data-ttu-id="2f2a7-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2f2a7-110">This example requires:</span></span>  
  
- <span data-ttu-id="2f2a7-111">Odkaz na projekt System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-111">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="2f2a7-112">Přístup ke členům <xref:System.ServiceProcess> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-112">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="2f2a7-113">Přidejte `Imports` příkaz, pokud ve svém kódu plně nekvalifikujete názvy členů.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-113">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="2f2a7-114">Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="2f2a7-114">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2f2a7-115">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="2f2a7-115">Robust Programming</span></span>  
 <span data-ttu-id="2f2a7-116"><xref:System.ServiceProcess.ServiceController.MachineName%2A>Vlastnost <xref:System.ServiceProcess.ServiceController> třídy je ve výchozím nastavení místní počítač.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-116">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="2f2a7-117">Chcete-li odkazovat na služby systému Windows na jiném počítači, změňte <xref:System.ServiceProcess.ServiceController.MachineName%2A> vlastnost na název počítače.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-117">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="2f2a7-118">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="2f2a7-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2f2a7-119">Službu nelze pozastavit.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-119">The service cannot be paused.</span></span> <span data-ttu-id="2f2a7-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="2f2a7-120">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="2f2a7-121">Při přístupu k rozhraní API systému došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="2f2a7-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="2f2a7-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="2f2a7-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2f2a7-123">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2f2a7-123">.NET Framework Security</span></span>  
 <span data-ttu-id="2f2a7-124">Řízení služeb v počítači může být omezeno pomocí nástroje <xref:System.ServiceProcess.ServiceControllerPermissionAccess> k nastavení oprávnění v nástroji <xref:System.ServiceProcess.ServiceControllerPermission> .</span><span class="sxs-lookup"><span data-stu-id="2f2a7-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="2f2a7-125">Přístup k informacím o službě může být omezen použitím sady <xref:System.Security.Permissions.PermissionState> k nastavení oprávnění v nástroji <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="2f2a7-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f2a7-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f2a7-126">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="2f2a7-127">Postupy: Pokračování služby systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f2a7-127">How to: Continue a Windows Service (Visual Basic)</span></span>](how-to-continue-a-windows-service-visual-basic.md)
