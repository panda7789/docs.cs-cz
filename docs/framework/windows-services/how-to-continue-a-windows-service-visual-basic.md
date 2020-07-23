---
title: 'Postupy: Pokračování služby systému Windows (Visual Basic)'
description: Přečtěte si, jak používat komponentu ServiceController k pokračování služby Windows (například služby Správce služby IIS) na místním počítači s Visual Basic.
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
ms.openlocfilehash: 2a04e330ea7dc37552053b2a7915909c011727f8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925784"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="4d58a-103">Postupy: Pokračování služby systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d58a-103">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="4d58a-104">Tento příklad používá <xref:System.ServiceProcess.ServiceController> komponentu k pokračování služby Správce služby IIS v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="4d58a-104">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d58a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d58a-105">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="4d58a-106">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="4d58a-106">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="4d58a-107">Ve výběru fragmentu kódu je umístěn v **operačním systému Windows > služby systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="4d58a-107">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="4d58a-108">Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="4d58a-108">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4d58a-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4d58a-109">Compiling the Code</span></span>  
 <span data-ttu-id="4d58a-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="4d58a-110">This example requires:</span></span>  
  
- <span data-ttu-id="4d58a-111">Odkaz na projekt System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="4d58a-111">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="4d58a-112">Přístup ke členům <xref:System.ServiceProcess> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4d58a-112">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="4d58a-113">Přidejte `Imports` příkaz, pokud ve svém kódu plně nekvalifikujete názvy členů.</span><span class="sxs-lookup"><span data-stu-id="4d58a-113">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="4d58a-114">Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="4d58a-114">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4d58a-115">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="4d58a-115">Robust Programming</span></span>  
 <span data-ttu-id="4d58a-116"><xref:System.ServiceProcess.ServiceController.MachineName%2A>Vlastnost <xref:System.ServiceProcess.ServiceController> třídy je ve výchozím nastavení místní počítač.</span><span class="sxs-lookup"><span data-stu-id="4d58a-116">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="4d58a-117">Chcete-li odkazovat na služby systému Windows na jiném počítači, změňte <xref:System.ServiceProcess.ServiceController.MachineName%2A> vlastnost na název počítače.</span><span class="sxs-lookup"><span data-stu-id="4d58a-117">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="4d58a-118">Metodu nelze volat <xref:System.ServiceProcess.ServiceController.Continue%2A> ve službě, dokud není stav řadiče služby <xref:System.ServiceProcess.ServiceControllerStatus.Paused> .</span><span class="sxs-lookup"><span data-stu-id="4d58a-118">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="4d58a-119">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="4d58a-119">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="4d58a-120">Službu nelze obnovit.</span><span class="sxs-lookup"><span data-stu-id="4d58a-120">The service cannot be resumed.</span></span> <span data-ttu-id="4d58a-121">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="4d58a-121">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="4d58a-122">Při přístupu k rozhraní API systému došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="4d58a-122">An error occurred when accessing a system API.</span></span> <span data-ttu-id="4d58a-123">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="4d58a-123">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4d58a-124">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4d58a-124">.NET Framework Security</span></span>  
 <span data-ttu-id="4d58a-125">Řízení služeb v počítači může být omezeno pomocí <xref:System.ServiceProcess.ServiceControllerPermissionAccess> výčtu k nastavení oprávnění ve <xref:System.ServiceProcess.ServiceControllerPermission> třídě.</span><span class="sxs-lookup"><span data-stu-id="4d58a-125">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="4d58a-126">Přístup k informacím o službě může být omezen pomocí <xref:System.Security.Permissions.PermissionState> výčtu k nastavení oprávnění ve <xref:System.Security.Permissions.SecurityPermission> třídě.</span><span class="sxs-lookup"><span data-stu-id="4d58a-126">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d58a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d58a-127">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [<span data-ttu-id="4d58a-128">Postupy: Pozastavení služby systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d58a-128">How to: Pause a Windows Service (Visual Basic)</span></span>](how-to-pause-a-windows-service-visual-basic.md)
