---
title: "Použití dvojitého ukládání do vyrovnávací paměti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5ad51e27c3d31ece1d11831c953023bedba3a97
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="using-double-buffering"></a><span data-ttu-id="16d10-102">Použití dvojitého ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="16d10-102">Using Double Buffering</span></span>
<span data-ttu-id="16d10-103">Grafiky s dvojitou vyrovnávací pamětí můžete použít ke snížení blikání v aplikacích, které obsahují komplexní vykreslovací operace.</span><span class="sxs-lookup"><span data-stu-id="16d10-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="16d10-104">Rozhraní .NET Framework obsahuje integrovanou podporu pro dvojité ukládání do vyrovnávací paměti, nebo můžete spravovat a vykreslení grafiky ručně.</span><span class="sxs-lookup"><span data-stu-id="16d10-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="16d10-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="16d10-105">In This Section</span></span>  
 [<span data-ttu-id="16d10-106">Dvojité grafiky uložené do vyrovnávací</span><span class="sxs-lookup"><span data-stu-id="16d10-106">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 <span data-ttu-id="16d10-107">Představuje dvojité vyrovnávací paměti koncept a jsou podrobněji popsány dále rozhraní .NET Framework podporu.</span><span class="sxs-lookup"><span data-stu-id="16d10-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="16d10-108">Postupy: omezení blikání grafiky pomocí dvojité vyrovnávací paměti pro formuláře a ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="16d10-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="16d10-109">Ukazuje, jak použít výchozí dvojité ukládání do vyrovnávací paměti podpora v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16d10-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="16d10-110">Postupy: ruční správa grafiky uložené do vyrovnávací</span><span class="sxs-lookup"><span data-stu-id="16d10-110">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="16d10-111">Ukazuje, jak spravovat dvojité vyrovnávací paměti v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="16d10-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="16d10-112">Postupy: ruční zobrazení grafiky uložené do vyrovnávací</span><span class="sxs-lookup"><span data-stu-id="16d10-112">How to: Manually Render Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="16d10-113">Ukazuje, jak k vykreslení grafiky s dvojitou vyrovnávací pamětí.</span><span class="sxs-lookup"><span data-stu-id="16d10-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="16d10-114">Odkaz</span><span class="sxs-lookup"><span data-stu-id="16d10-114">Reference</span></span>  
 <span data-ttu-id="16d10-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span><span class="sxs-lookup"><span data-stu-id="16d10-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span></span>  
 <span data-ttu-id="16d10-116">Ovládací prvek metoda, která umožňuje dvojité ukládání do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="16d10-116">Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="16d10-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span><span class="sxs-lookup"><span data-stu-id="16d10-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span></span>  
 <span data-ttu-id="16d10-118">Poskytuje metody pro vytváření grafických vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="16d10-118">Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="16d10-119">Poskytuje přístup k grafiky uložené ve vyrovnávací paměti kontextu pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="16d10-119">Provides access to the buffered graphics context for a application domain.</span></span>
