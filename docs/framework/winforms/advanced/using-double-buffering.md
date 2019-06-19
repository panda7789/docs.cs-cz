---
title: Použití dvojitého ukládání do vyrovnávací paměti
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: 5b22336221c7bdda3c9dd7adf23308a2b0bad450
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169911"
---
# <a name="using-double-buffering"></a><span data-ttu-id="5da43-102">Použití dvojitého ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="5da43-102">Using Double Buffering</span></span>
<span data-ttu-id="5da43-103">Grafiky s dvojitou vyrovnávací pamětí můžete použít k omezení blikání v aplikacích, které obsahují komplexní Malování operace.</span><span class="sxs-lookup"><span data-stu-id="5da43-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="5da43-104">Rozhraní .NET Framework obsahuje integrovanou podporu dvojité ukládání do vyrovnávací paměti nebo můžete spravovat a ruční zobrazení grafiky.</span><span class="sxs-lookup"><span data-stu-id="5da43-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5da43-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5da43-105">In This Section</span></span>  
 [<span data-ttu-id="5da43-106">Grafiky s dvojitou vyrovnávací pamětí</span><span class="sxs-lookup"><span data-stu-id="5da43-106">Double Buffered Graphics</span></span>](double-buffered-graphics.md)  
 <span data-ttu-id="5da43-107">Zavádí dvojité vyrovnávací paměti koncept a jsou podrobněji popsány dále podpora rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5da43-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="5da43-108">Postupy: Omezení blikání grafiky dvojité ukládání do vyrovnávací paměti pro formuláře a ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="5da43-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="5da43-109">Ukazuje, jak použít výchozí dvojité ukládání do vyrovnávací paměti podpora v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5da43-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="5da43-110">Postupy: Ruční správa grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="5da43-110">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="5da43-111">Ukazuje, jak spravovat dvojité ukládání do vyrovnávací paměti v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="5da43-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="5da43-112">Postupy: Ruční zobrazení grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="5da43-112">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="5da43-113">Ukazuje, jak pro vykreslení grafiky s dvojitou vyrovnávací pamětí.</span><span class="sxs-lookup"><span data-stu-id="5da43-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5da43-114">Odkaz</span><span class="sxs-lookup"><span data-stu-id="5da43-114">Reference</span></span>  
 <span data-ttu-id="5da43-115"><xref:System.Windows.Forms.Control.SetStyle%2A> Metoda ovládací prvek, který umožňuje dvojité ukládání do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5da43-115"><xref:System.Windows.Forms.Control.SetStyle%2A> Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="5da43-116"><xref:System.Drawing.BufferedGraphicsContext> Poskytuje metody pro vytváření grafické vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5da43-116"><xref:System.Drawing.BufferedGraphicsContext> Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="5da43-117">Poskytuje přístup ke kontextu grafiky uložené do vyrovnávací paměti pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="5da43-117">Provides access to the buffered graphics context for a application domain.</span></span>
