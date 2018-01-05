---
title: "Windows Forms a nespravované aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2672e8f87b28e81a9aa233cbf0f1b2c24b2239c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="289ab-102">Windows Forms a nespravované aplikace</span><span class="sxs-lookup"><span data-stu-id="289ab-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="289ab-103">Aplikace Windows Forms a ovládacích prvků můžete spolupracovat s nespravovaných aplikací se některých aspektů.</span><span class="sxs-lookup"><span data-stu-id="289ab-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="289ab-104">Následující části popisují scénáře a konfigurace, které podporují aplikace a ovládací prvky Windows Forms a ty, které nepodporují.</span><span class="sxs-lookup"><span data-stu-id="289ab-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="289ab-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="289ab-105">In This Section</span></span>  
 [<span data-ttu-id="289ab-106">Přehled modelu Windows Forms a nespravovaných aplikací</span><span class="sxs-lookup"><span data-stu-id="289ab-106">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="289ab-107">Poskytuje obecné informace o tom, jak použít a implementovat ovládací prvky Windows Forms, které pracují s nespravované aplikace.</span><span class="sxs-lookup"><span data-stu-id="289ab-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="289ab-108">Postupy: Podpora zprostředkovatele komunikace s objekty COM zobrazením formuláře Windows pomocí metody ShowDialog</span><span class="sxs-lookup"><span data-stu-id="289ab-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="289ab-109">Poskytuje příklad kódu, který ukazuje způsob použití <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> metodu pro spuštění Windows Form v nespravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="289ab-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="289ab-110">Postupy: Podpora komunikace s objekty COM zobrazením jednotlivých formulářů Windows ve vlastním vlákně</span><span class="sxs-lookup"><span data-stu-id="289ab-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="289ab-111">Poskytuje příklad kódu, který ukazuje, jak spustit formuláře Windows ve vlastním vlákně.</span><span class="sxs-lookup"><span data-stu-id="289ab-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="289ab-112">Viz také [návod: podpora spoluprací COM zobrazení každý formuláři Windows v její vlastní vláken](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="289ab-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="289ab-113">Odkaz</span><span class="sxs-lookup"><span data-stu-id="289ab-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="289ab-114">Umožňuje vytvořit samostatný podproces pro formuláře systému Windows.</span><span class="sxs-lookup"><span data-stu-id="289ab-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="289ab-115">Zahájí cyklus zpráv vlákna.</span><span class="sxs-lookup"><span data-stu-id="289ab-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="289ab-116">Zařazuje volání z aplikace bez správy do formuláře.</span><span class="sxs-lookup"><span data-stu-id="289ab-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="289ab-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="289ab-117">Related Sections</span></span>  
 [<span data-ttu-id="289ab-118">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="289ab-118">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="289ab-119">Poskytuje obecné informace o tom, jak používat typy rozhraní .NET Framework v nespravovaných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="289ab-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
