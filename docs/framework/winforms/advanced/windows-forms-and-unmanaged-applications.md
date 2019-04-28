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
ms.openlocfilehash: 65465f22b1806d385523c894cce2103afe33c2f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746696"
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="a8cb3-102">Windows Forms a nespravované aplikace</span><span class="sxs-lookup"><span data-stu-id="a8cb3-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="a8cb3-103">Aplikace Windows Forms a ovládacích prvků můžete spolupracovat s nespravované aplikace, se některé upozornění.</span><span class="sxs-lookup"><span data-stu-id="a8cb3-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="a8cb3-104">Následující části popisují scénáře a konfigurace, které podporují aplikace a ovládací prvky Windows Forms a ty, které nepodporují.</span><span class="sxs-lookup"><span data-stu-id="a8cb3-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8cb3-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a8cb3-105">In This Section</span></span>  
 [<span data-ttu-id="a8cb3-106">Přehled modelu Windows Forms a nespravovaných aplikací</span><span class="sxs-lookup"><span data-stu-id="a8cb3-106">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="a8cb3-107">Poskytuje obecné informace o tom, jak používat a implementaci ovládacích prvků Windows Forms, které pracují s nespravovanými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="a8cb3-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="a8cb3-108">Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="a8cb3-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="a8cb3-109">Obsahuje příklad kódu, který ukazuje způsob použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> způsob spuštění formulář Windows v nespravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8cb3-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="a8cb3-110">Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně</span><span class="sxs-lookup"><span data-stu-id="a8cb3-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="a8cb3-111">Obsahuje příklad kódu, který ukazuje, jak spustit formulářů Windows ve vlastním vlákně.</span><span class="sxs-lookup"><span data-stu-id="a8cb3-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="a8cb3-112">Viz také [názorný postup: Podpora zprostředkovatele komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a8cb3-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a8cb3-113">Odkaz</span><span class="sxs-lookup"><span data-stu-id="a8cb3-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="a8cb3-114">Použít k vytvoření samostatného vlákna pro formulář Windows.</span><span class="sxs-lookup"><span data-stu-id="a8cb3-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="a8cb3-115">Spustí se smyčkou zpráv pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="a8cb3-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="a8cb3-116">Zařadí volání z nespravovaného aplikace do formuláře.</span><span class="sxs-lookup"><span data-stu-id="a8cb3-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8cb3-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a8cb3-117">Related Sections</span></span>  
 [<span data-ttu-id="a8cb3-118">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="a8cb3-118">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="a8cb3-119">Poskytuje obecné informace o tom, jak používat typy rozhraní .NET Framework v nespravovaných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="a8cb3-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
