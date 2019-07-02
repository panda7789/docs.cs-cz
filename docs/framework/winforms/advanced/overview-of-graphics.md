---
title: Přehled grafiky
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505319"
---
# <a name="overview-of-graphics"></a><span data-ttu-id="1994a-102">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="1994a-102">Overview of Graphics</span></span>
<span data-ttu-id="1994a-103">Rozhraní GDI + je aplikační programovací rozhraní (API), která tvoří subsystému operačního systému Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="1994a-103">GDI+ is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> <span data-ttu-id="1994a-104">Rozhraní GDI + je zodpovědná za zobrazení informací na obrazovkách a tiskárny.</span><span class="sxs-lookup"><span data-stu-id="1994a-104">GDI+ is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="1994a-105">Jak název napovídá, rozhraní GDI + je nástupcem GDI Graphics Device Interface zahrnuté ve starších verzích Windows.</span><span class="sxs-lookup"><span data-stu-id="1994a-105">As its name suggests, GDI+ is the successor to GDI, the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="1994a-106">Spravované třídy rozhraní</span><span class="sxs-lookup"><span data-stu-id="1994a-106">Managed Class Interface</span></span>  
 <span data-ttu-id="1994a-107">Rozhraní API je přístupný prostřednictvím sady tříd nasadit jako spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="1994a-107">The GDI+ API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="1994a-108">Tato sada třídy se nazývá *spravovanou třídu rozhraní* do rozhraní GDI +.</span><span class="sxs-lookup"><span data-stu-id="1994a-108">This set of classes is called the *managed class interface* to GDI+.</span></span> <span data-ttu-id="1994a-109">Následující obory názvů tvoří rozhraní spravovanou třídu:</span><span class="sxs-lookup"><span data-stu-id="1994a-109">The following namespaces make up the managed class interface:</span></span>  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="1994a-110">S Graphics Device Interface, jako je například rozhraní GDI + můžete zobrazit informace na obrazovce nebo tiskárny, nemusíte mít obavy o podrobnostech konkrétní zobrazovací zařízení.</span><span class="sxs-lookup"><span data-stu-id="1994a-110">With a Graphics Device Interface, such as GDI+, you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="1994a-111">Programátor volá metody poskytované objektem třídy rozhraní GDI +.</span><span class="sxs-lookup"><span data-stu-id="1994a-111">The programmer makes calls to methods provided by GDI+ classes.</span></span> <span data-ttu-id="1994a-112">Tyto metody zase volání odpovídající ovladače pro konkrétní zařízení.</span><span class="sxs-lookup"><span data-stu-id="1994a-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> <span data-ttu-id="1994a-113">Rozhraní GDI + insulates aplikace od hardwaru grafiky.</span><span class="sxs-lookup"><span data-stu-id="1994a-113">GDI+ insulates the application from the graphics hardware.</span></span> <span data-ttu-id="1994a-114">Je tato izolace, která umožňuje programátorem na vytvoření aplikace nezávislých na zařízení.</span><span class="sxs-lookup"><span data-stu-id="1994a-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1994a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1994a-115">See also</span></span>

- [<span data-ttu-id="1994a-116">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="1994a-116">Graphics Overview</span></span>](graphics-overview-windows-forms.md)
