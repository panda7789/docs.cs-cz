---
title: Přehled grafiky
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: 8d8e1ab286d4e5723f5ca6bca0b6eeff53ac1d43
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711340"
---
# <a name="overview-of-graphics"></a><span data-ttu-id="4e230-102">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="4e230-102">Overview of Graphics</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="4e230-103">je aplikační programovací rozhraní (API), která tvoří subsystému operačního systému Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="4e230-103">is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="4e230-104">je zodpovědná za zobrazení informací na obrazovkách a tiskárny.</span><span class="sxs-lookup"><span data-stu-id="4e230-104">is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="4e230-105">Jak název napovídá, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] je nástupcem [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], Graphics Device Interface zahrnuté ve starších verzích Windows.</span><span class="sxs-lookup"><span data-stu-id="4e230-105">As its name suggests, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is the successor to [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="4e230-106">Spravované třídy rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e230-106">Managed Class Interface</span></span>  
 <span data-ttu-id="4e230-107">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Rozhraní API je k dispozici prostřednictvím sady tříd nasadit jako spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="4e230-107">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="4e230-108">Tato sada třídy se nazývá *spravovanou třídu rozhraní* k [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e230-108">This set of classes is called the *managed class interface* to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="4e230-109">Následující obory názvů tvoří rozhraní spravovanou třídu:</span><span class="sxs-lookup"><span data-stu-id="4e230-109">The following namespaces make up the managed class interface:</span></span>  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="4e230-110">S Graphics Device Interface jako například [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], aniž byste museli mít obavy o podrobnostech konkrétní zobrazovací zařízení můžete zobrazit informace na obrazovce nebo tiskárny.</span><span class="sxs-lookup"><span data-stu-id="4e230-110">With a Graphics Device Interface, such as [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="4e230-111">Programátor provede volání do metody poskytované [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] třídy.</span><span class="sxs-lookup"><span data-stu-id="4e230-111">The programmer makes calls to methods provided by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span> <span data-ttu-id="4e230-112">Tyto metody zase volání odpovídající ovladače pro konkrétní zařízení.</span><span class="sxs-lookup"><span data-stu-id="4e230-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="4e230-113">insulates aplikace od hardwaru grafiky.</span><span class="sxs-lookup"><span data-stu-id="4e230-113">insulates the application from the graphics hardware.</span></span> <span data-ttu-id="4e230-114">Je tato izolace, která umožňuje programátorem na vytvoření aplikace nezávislých na zařízení.</span><span class="sxs-lookup"><span data-stu-id="4e230-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e230-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e230-115">See also</span></span>
- [<span data-ttu-id="4e230-116">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="4e230-116">Graphics Overview</span></span>](graphics-overview-windows-forms.md)
