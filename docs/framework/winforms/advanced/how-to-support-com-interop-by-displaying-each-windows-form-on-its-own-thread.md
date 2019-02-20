---
title: 'Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 91c0b6384d8c39848cfd199950034d2f62e716df
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441749"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="52264-102">Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně</span><span class="sxs-lookup"><span data-stu-id="52264-102">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>
<span data-ttu-id="52264-103">Vyřešíte problémy vzájemná funkční spolupráce modelu COM zobrazením formuláře ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] smyčky zpráv, které můžete vytvořit pomocí <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="52264-103">You can resolve COM interoperability problems by displaying your form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="52264-104">Chcete-li pracovní formulář Windows správně z klientské aplikace modelu COM, musíte spustit formuláře na smyčku zpráv Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="52264-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="52264-105">K tomuto účelu použijte jednu z následujících postupů:</span><span class="sxs-lookup"><span data-stu-id="52264-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="52264-106">Použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro zobrazení formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="52264-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="52264-107">Další informace najdete v tématu [jak: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="52264-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span></span>  
  
-   <span data-ttu-id="52264-108">Každý formulář Windows pro zobrazení na samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="52264-108">Display each Windows Form on a separate thread.</span></span>  
  
 <span data-ttu-id="52264-109">Není k dispozici rozsáhlou podporu pro tuto funkci v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="52264-109">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="52264-110">Viz také [názorný postup: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="52264-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52264-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="52264-111">Example</span></span>  
 <span data-ttu-id="52264-112">Následující příklad kódu ukazuje, jak formulář pro zobrazení v samostatném vlákně a volání <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metodu spustit pumpu zpráv Windows Forms v daném vláknu.</span><span class="sxs-lookup"><span data-stu-id="52264-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="52264-113">Chcete-li tuto metodu použijte, musí zařaďte všechna volání do formuláře z nespravovaných aplikací s použitím <xref:System.Windows.Forms.Control.Invoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="52264-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>  
  
 <span data-ttu-id="52264-114">Tento přístup vyžaduje, že každá instance formuláře je spuštěna ve vlastním vlákně s použitím vlastní smyčky zpráv.</span><span class="sxs-lookup"><span data-stu-id="52264-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="52264-115">Nemůžete mít více než jeden smyčky zpráv spuštěná na vlákno.</span><span class="sxs-lookup"><span data-stu-id="52264-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="52264-116">Proto nelze změnit smyčky zpráv klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="52264-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="52264-117">Však můžete změnit [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] součásti spustit nové vlákno, která používá vlastní smyčku zpráv.</span><span class="sxs-lookup"><span data-stu-id="52264-117">However, you can modify the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component to start a new thread that uses its own message loop.</span></span>  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="52264-118">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="52264-118">Compiling the Code</span></span>  
  
-   <span data-ttu-id="52264-119">Kompilace `COMForm`, `Form1`, a `FormManager` typů do sestavení volá `COMWinform.dll`.</span><span class="sxs-lookup"><span data-stu-id="52264-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="52264-120">Registrace sestavení zprostředkovatele komunikace s objekty modelu COM pomocí jedné z metod popsaných v [zabalení sestavení pro model COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="52264-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="52264-121">Teď můžete použít sestavení a jeho odpovídající soubor knihovny (.tlb) typů v nespravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="52264-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="52264-122">Například můžete použít knihovnu typů jako odkaz v projektu jazyka Visual Basic 6.0 spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="52264-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52264-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52264-123">See also</span></span>
- [<span data-ttu-id="52264-124">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="52264-124">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="52264-125">Zabalení sestavení pro model COM</span><span class="sxs-lookup"><span data-stu-id="52264-125">Packaging an Assembly for COM</span></span>](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)
- [<span data-ttu-id="52264-126">Registrování sestav pomocí modelu COM</span><span class="sxs-lookup"><span data-stu-id="52264-126">Registering Assemblies with COM</span></span>](../../../../docs/framework/interop/registering-assemblies-with-com.md)
- [<span data-ttu-id="52264-127">Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="52264-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)
- [<span data-ttu-id="52264-128">Přehled modelu Windows Forms a nespravovaných aplikací</span><span class="sxs-lookup"><span data-stu-id="52264-128">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
