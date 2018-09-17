---
title: Windows Forms a nespravované aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: bc0c848d1c92871dacab93497c674645f3ac83fe
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45742979"
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="c0314-102">Windows Forms a nespravované aplikace</span><span class="sxs-lookup"><span data-stu-id="c0314-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="c0314-103">Aplikace Windows Forms a ovládacích prvků můžete spolupracovat s nespravované aplikace, se některé upozornění.</span><span class="sxs-lookup"><span data-stu-id="c0314-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="c0314-104">Následující části popisují scénáře a konfigurace, které podporují aplikace a ovládací prvky Windows Forms a ty, které nepodporují.</span><span class="sxs-lookup"><span data-stu-id="c0314-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0314-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c0314-105">In This Section</span></span>  
 [<span data-ttu-id="c0314-106">Přehled modelu Windows Forms a nespravovaných aplikací</span><span class="sxs-lookup"><span data-stu-id="c0314-106">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="c0314-107">Poskytuje obecné informace o tom, jak používat a implementaci ovládacích prvků Windows Forms, které pracují s nespravovanými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="c0314-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="c0314-108">Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="c0314-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="c0314-109">Obsahuje příklad kódu, který ukazuje způsob použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> způsob spuštění formulář Windows v nespravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="c0314-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="c0314-110">Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně</span><span class="sxs-lookup"><span data-stu-id="c0314-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="c0314-111">Obsahuje příklad kódu, který ukazuje, jak spustit formulářů Windows ve vlastním vlákně.</span><span class="sxs-lookup"><span data-stu-id="c0314-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="c0314-112">Viz také [návod: podpora komunikace s objekty COM zobrazení každý formulář Windows na jeho vlastní vlákně](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c0314-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c0314-113">Odkaz</span><span class="sxs-lookup"><span data-stu-id="c0314-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="c0314-114">Použít k vytvoření samostatného vlákna pro formulář Windows.</span><span class="sxs-lookup"><span data-stu-id="c0314-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="c0314-115">Spustí se smyčkou zpráv pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="c0314-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="c0314-116">Zařadí volání z nespravovaného aplikace do formuláře.</span><span class="sxs-lookup"><span data-stu-id="c0314-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c0314-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c0314-117">Related Sections</span></span>  
 [<span data-ttu-id="c0314-118">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="c0314-118">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="c0314-119">Poskytuje obecné informace o tom, jak používat typy rozhraní .NET Framework v nespravovaných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="c0314-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
