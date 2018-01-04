---
title: "Přehled grafiky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3438fe2f1c3a6fc40efda0ff2583208f38bf7d5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-graphics"></a><span data-ttu-id="37a9e-102">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="37a9e-102">Overview of Graphics</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="37a9e-103">je programovací rozhraní aplikace (API), která tvoří subsystém operačního systému Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="37a9e-103"> is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="37a9e-104">zodpovídá za zobrazení informací na obrazovky a tiskárny.</span><span class="sxs-lookup"><span data-stu-id="37a9e-104"> is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="37a9e-105">Jak naznačuje název [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] je nástupcem [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], rozhraní grafických zařízení, která je zahrnutá v dřívějších verzích systému Windows.</span><span class="sxs-lookup"><span data-stu-id="37a9e-105">As its name suggests, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is the successor to [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="37a9e-106">Spravované třídy rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a9e-106">Managed Class Interface</span></span>  
 <span data-ttu-id="37a9e-107">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Rozhraní API je k dispozici prostřednictvím sadu tříd, které jsou nasazeny jako spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="37a9e-107">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="37a9e-108">Tato sada třídy se nazývá *spravované třídy rozhraní* k [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37a9e-108">This set of classes is called the *managed class interface* to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="37a9e-109">Následující obory názvů tvoří rozhraní spravované třídy:</span><span class="sxs-lookup"><span data-stu-id="37a9e-109">The following namespaces make up the managed class interface:</span></span>  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="37a9e-110">Zařízení rozhraní grafiky jako například [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], bez nutnosti starat o podrobnosti o konkrétní zobrazení zařízení můžete zobrazit informace na obrazovce nebo tiskárny.</span><span class="sxs-lookup"><span data-stu-id="37a9e-110">With a Graphics Device Interface, such as [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="37a9e-111">Programátorů provádí volání do metody poskytované [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] třídy.</span><span class="sxs-lookup"><span data-stu-id="37a9e-111">The programmer makes calls to methods provided by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span> <span data-ttu-id="37a9e-112">Tyto metody se pak volání příslušné konkrétní ovladače.</span><span class="sxs-lookup"><span data-stu-id="37a9e-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="37a9e-113">insulates aplikace v grafickém hardwaru.</span><span class="sxs-lookup"><span data-stu-id="37a9e-113"> insulates the application from the graphics hardware.</span></span> <span data-ttu-id="37a9e-114">Je tato izolace, která umožňuje programátory k vytvoření nezávislé na zařízení aplikací.</span><span class="sxs-lookup"><span data-stu-id="37a9e-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37a9e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="37a9e-115">See Also</span></span>  
 [<span data-ttu-id="37a9e-116">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="37a9e-116">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)
