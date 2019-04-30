---
title: Použití dvojitého ukládání do vyrovnávací paměti
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: ac6c9b7f2cc1fea86a75eaaf4a2dde1ea60e4f40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777153"
---
# <a name="using-double-buffering"></a><span data-ttu-id="f1e9b-102">Použití dvojitého ukládání do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="f1e9b-102">Using Double Buffering</span></span>
<span data-ttu-id="f1e9b-103">Grafiky s dvojitou vyrovnávací pamětí můžete použít k omezení blikání v aplikacích, které obsahují komplexní Malování operace.</span><span class="sxs-lookup"><span data-stu-id="f1e9b-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="f1e9b-104">Rozhraní .NET Framework obsahuje integrovanou podporu dvojité ukládání do vyrovnávací paměti nebo můžete spravovat a ruční zobrazení grafiky.</span><span class="sxs-lookup"><span data-stu-id="f1e9b-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1e9b-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f1e9b-105">In This Section</span></span>  
 [<span data-ttu-id="f1e9b-106">Grafiky s dvojitou vyrovnávací pamětí</span><span class="sxs-lookup"><span data-stu-id="f1e9b-106">Double Buffered Graphics</span></span>](double-buffered-graphics.md)  
 <span data-ttu-id="f1e9b-107">Zavádí dvojité vyrovnávací paměti koncept a jsou podrobněji popsány dále podpora rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1e9b-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="f1e9b-108">Postupy: Omezení blikání grafiky dvojité ukládání do vyrovnávací paměti pro formuláře a ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="f1e9b-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="f1e9b-109">Ukazuje, jak použít výchozí dvojité ukládání do vyrovnávací paměti podpora v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1e9b-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="f1e9b-110">Postupy: Ruční správa grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="f1e9b-110">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="f1e9b-111">Ukazuje, jak spravovat dvojité ukládání do vyrovnávací paměti v aplikacích.</span><span class="sxs-lookup"><span data-stu-id="f1e9b-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="f1e9b-112">Postupy: Ruční zobrazení grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="f1e9b-112">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="f1e9b-113">Ukazuje, jak pro vykreslení grafiky s dvojitou vyrovnávací pamětí.</span><span class="sxs-lookup"><span data-stu-id="f1e9b-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f1e9b-114">Odkaz</span><span class="sxs-lookup"><span data-stu-id="f1e9b-114">Reference</span></span>  
 <span data-ttu-id="f1e9b-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span><span class="sxs-lookup"><span data-stu-id="f1e9b-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span></span>  
 <span data-ttu-id="f1e9b-116">Metoda ovládací prvek, který umožňuje dvojité ukládání do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f1e9b-116">Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="f1e9b-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span><span class="sxs-lookup"><span data-stu-id="f1e9b-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span></span>  
 <span data-ttu-id="f1e9b-118">Poskytuje metody pro vytváření grafické vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f1e9b-118">Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="f1e9b-119">Poskytuje přístup ke kontextu grafiky uložené do vyrovnávací paměti pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1e9b-119">Provides access to the buffered graphics context for a application domain.</span></span>
