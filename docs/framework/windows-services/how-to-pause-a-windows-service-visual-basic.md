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
manager: douge
ms.openlocfilehash: 43a852f1b618582c5aa65636e0a529434f8fd6a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="ec22f-102">Postupy: Pozastavení služby systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec22f-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="ec22f-103">Tento příklad používá <xref:System.ServiceProcess.ServiceController> součásti pozastavit službu Správce služby IIS v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="ec22f-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec22f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec22f-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="ec22f-105">Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="ec22f-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="ec22f-106">V Sběrač fragmentů kódu je umístěn v **operačního systému Windows > služby systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="ec22f-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="ec22f-107">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="ec22f-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ec22f-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ec22f-108">Compiling the Code</span></span>  
 <span data-ttu-id="ec22f-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ec22f-109">This example requires:</span></span>  
  
-   <span data-ttu-id="ec22f-110">Odkaz na projekt na System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="ec22f-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="ec22f-111">Přístup k členům <xref:System.ServiceProcess> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ec22f-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="ec22f-112">Přidat `Imports` příkaz, pokud jste nejsou kvalifikující plně názvy členů v kódu.</span><span class="sxs-lookup"><span data-stu-id="ec22f-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="ec22f-113">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="ec22f-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ec22f-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ec22f-114">Robust Programming</span></span>  
 <span data-ttu-id="ec22f-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Vlastnost <xref:System.ServiceProcess.ServiceController> třída je ve výchozím nastavení místním počítači.</span><span class="sxs-lookup"><span data-stu-id="ec22f-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="ec22f-116">Chcete-li služby systému Windows na jiný počítač, změňte <xref:System.ServiceProcess.ServiceController.MachineName%2A> vlastnost na název tohoto počítače.</span><span class="sxs-lookup"><span data-stu-id="ec22f-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="ec22f-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="ec22f-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ec22f-118">Službu nelze pozastavit.</span><span class="sxs-lookup"><span data-stu-id="ec22f-118">The service cannot be paused.</span></span> <span data-ttu-id="ec22f-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="ec22f-119">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="ec22f-120">Došlo k chybě při přístupu k systému rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ec22f-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="ec22f-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="ec22f-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ec22f-122">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ec22f-122">.NET Framework Security</span></span>  
 <span data-ttu-id="ec22f-123">Řízení služeb v počítači může být omezena pomocí <xref:System.ServiceProcess.ServiceControllerPermissionAccess> nastavit oprávnění <xref:System.ServiceProcess.ServiceControllerPermission>.</span><span class="sxs-lookup"><span data-stu-id="ec22f-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="ec22f-124">Přístup k informacím o služby může být omezena pomocí <xref:System.Security.Permissions.PermissionState> nastavit oprávnění <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="ec22f-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec22f-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec22f-125">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>  
 [<span data-ttu-id="ec22f-126">Postupy: Pokračování služby systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec22f-126">How to: Continue a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
