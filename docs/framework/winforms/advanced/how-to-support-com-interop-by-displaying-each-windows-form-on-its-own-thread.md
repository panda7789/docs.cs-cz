---
title: "Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60e52bc1486f74bdce44062a4ac861032b7b660c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="1d490-102">Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně</span><span class="sxs-lookup"><span data-stu-id="1d490-102">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>
<span data-ttu-id="1d490-103">Můžete vyřešit problémy vzájemná funkční spolupráce COM zobrazení formuláře v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ve smyčce zpráv, které můžete vytvořit pomocí <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="1d490-103">You can resolve COM interoperability problems by displaying your form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="1d490-104">Chcete-li pracovní formuláře Windows správně z klientské aplikace modelu COM, musíte spustit formuláře ve smyčce zpráv Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1d490-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="1d490-105">K tomuto účelu použijte jednu z následujících postupů:</span><span class="sxs-lookup"><span data-stu-id="1d490-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="1d490-106">Použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro zobrazení formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="1d490-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="1d490-107">Další informace najdete v tématu [postupy: podpora spoluprací COM zobrazením Windows Form pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="1d490-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span></span>  
  
-   <span data-ttu-id="1d490-108">Zobrazení jednotlivých formulářů Windows na samostatné vlákno.</span><span class="sxs-lookup"><span data-stu-id="1d490-108">Display each Windows Form on a separate thread.</span></span>  
  
 <span data-ttu-id="1d490-109">Je rozsáhlá podpora pro tuto funkci v [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1d490-109">There is extensive support for this feature in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="1d490-110">Viz také [návod: podpora spoluprací COM zobrazení každý formuláři Windows v její vlastní vláken](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1d490-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d490-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d490-111">Example</span></span>  
 <span data-ttu-id="1d490-112">Následující příklad kódu ukazuje, jak zobrazit formulář na samostatné vlákno a volání <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metoda zahájíte zprávy odeslané Windows Forms v daném vláknu.</span><span class="sxs-lookup"><span data-stu-id="1d490-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="1d490-113">Chcete-li použít tuto metodu, musí zařazování žádné volání do formuláře z nespravované aplikace pomocí <xref:System.Windows.Forms.Control.Invoke%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1d490-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>  
  
 <span data-ttu-id="1d490-114">Tento postup vyžaduje, že každá instance ve tvaru, který spouští ve vlastním vlákně pomocí vlastní zpráva smyčky.</span><span class="sxs-lookup"><span data-stu-id="1d490-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="1d490-115">Nemůže mít více než jeden smyčku zpráva spuštěna na vlákno.</span><span class="sxs-lookup"><span data-stu-id="1d490-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="1d490-116">Proto nelze změnit smyčce zpráv klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="1d490-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="1d490-117">Však můžete upravit [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] součásti spustit nové vlákno, která používá vlastní zpráva smyčky.</span><span class="sxs-lookup"><span data-stu-id="1d490-117">However, you can modify the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component to start a new thread that uses its own message loop.</span></span>  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d490-118">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1d490-118">Compiling the Code</span></span>  
  
-   <span data-ttu-id="1d490-119">Kompilace `COMForm`, `Form1`, a `FormManager` názvem typy v sestavení `COMWinform.dll`.</span><span class="sxs-lookup"><span data-stu-id="1d490-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="1d490-120">Registrace sestavení pro zprostředkovatel komunikace s objekty modelu COM pomocí jedné z metod popsaných v [balení sestavení pro model COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="1d490-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="1d490-121">Teď můžete použít sestavení a jeho odpovídající soubor typu knihovny (.tlb) v nespravovaných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="1d490-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="1d490-122">Například můžete použít knihovny typů jako odkaz v projektu jazyka Visual Basic 6.0 spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="1d490-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d490-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d490-123">See Also</span></span>  
 [<span data-ttu-id="1d490-124">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="1d490-124">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="1d490-125">Zabalení sestavení pro model COM</span><span class="sxs-lookup"><span data-stu-id="1d490-125">Packaging an Assembly for COM</span></span>](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [<span data-ttu-id="1d490-126">Registrování sestav pomocí modelu COM</span><span class="sxs-lookup"><span data-stu-id="1d490-126">Registering Assemblies with COM</span></span>](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [<span data-ttu-id="1d490-127">Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="1d490-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [<span data-ttu-id="1d490-128">Přehled modelu Windows Forms a nespravovaných aplikací</span><span class="sxs-lookup"><span data-stu-id="1d490-128">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
