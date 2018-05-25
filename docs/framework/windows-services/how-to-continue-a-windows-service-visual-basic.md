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
manager: douge
ms.openlocfilehash: 15ef15e0afe43d56db0972a686cd093e22c672dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="4863b-102">Postupy: Pokračování služby systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4863b-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="4863b-103">Tento příklad používá <xref:System.ServiceProcess.ServiceController> součást pokračujte Správa služby IIS v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="4863b-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4863b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4863b-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="4863b-105">Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="4863b-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="4863b-106">V Sběrač fragmentů kódu je umístěn v **operačního systému Windows > služby systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="4863b-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="4863b-107">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="4863b-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4863b-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4863b-108">Compiling the Code</span></span>  
 <span data-ttu-id="4863b-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="4863b-109">This example requires:</span></span>  
  
-   <span data-ttu-id="4863b-110">Odkaz na projekt na System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="4863b-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="4863b-111">Přístup k členům <xref:System.ServiceProcess> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4863b-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="4863b-112">Přidat `Imports` příkaz, pokud jste nejsou kvalifikující plně názvy členů v kódu.</span><span class="sxs-lookup"><span data-stu-id="4863b-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="4863b-113">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="4863b-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4863b-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="4863b-114">Robust Programming</span></span>  
 <span data-ttu-id="4863b-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Vlastnost <xref:System.ServiceProcess.ServiceController> třída je ve výchozím nastavení místním počítači.</span><span class="sxs-lookup"><span data-stu-id="4863b-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="4863b-116">Chcete-li služby systému Windows na jiný počítač, změňte <xref:System.ServiceProcess.ServiceController.MachineName%2A> vlastnost na název tohoto počítače.</span><span class="sxs-lookup"><span data-stu-id="4863b-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="4863b-117">Nelze volat <xref:System.ServiceProcess.ServiceController.Continue%2A> metoda na službě, dokud je stav služby řadiče <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span><span class="sxs-lookup"><span data-stu-id="4863b-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="4863b-118">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="4863b-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="4863b-119">Službu nelze obnovit.</span><span class="sxs-lookup"><span data-stu-id="4863b-119">The service cannot be resumed.</span></span> <span data-ttu-id="4863b-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="4863b-120">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="4863b-121">Došlo k chybě při přístupu k systému rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="4863b-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="4863b-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="4863b-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4863b-123">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4863b-123">.NET Framework Security</span></span>  
 <span data-ttu-id="4863b-124">Řízení služeb v počítači může být omezena pomocí <xref:System.ServiceProcess.ServiceControllerPermissionAccess> výčtu nastavit oprávnění <xref:System.ServiceProcess.ServiceControllerPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="4863b-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="4863b-125">Přístup k informacím o služby může být omezena pomocí <xref:System.Security.Permissions.PermissionState> výčtu nastavit oprávnění <xref:System.Security.Permissions.SecurityPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="4863b-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4863b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="4863b-126">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [<span data-ttu-id="4863b-127">Postupy: Pozastavení služby systému Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4863b-127">How to: Pause a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
