---
title: "Windows Forms – souřadnice"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f4b42fd71dacb0071013067dc3c14add96c8aca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-coordinates"></a><span data-ttu-id="bb3b4-102">Windows Forms – souřadnice</span><span class="sxs-lookup"><span data-stu-id="bb3b4-102">Windows Forms Coordinates</span></span>
<span data-ttu-id="bb3b4-103">Souřadnicový systém pro formuláře Windows je založený na zařízení souřadnice a základní měrná jednotka služby při kreslení v systému Windows Forms je jednotka zařízení (obvykle pixelů).</span><span class="sxs-lookup"><span data-stu-id="bb3b4-103">The coordinate system for a Windows Form is based on device coordinates, and the basic unit of measure when drawing in Windows Forms is the device unit (typically, the pixel).</span></span> <span data-ttu-id="bb3b4-104">Bodů na obrazovce jsou popsané podle dvojic souřadnice x a y s souřadnice x zvýšení souřadnice y zvýšení shora dolů a doprava.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-104">Points on the screen are described by x- and y-coordinate pairs, with the x-coordinates increasing to the right and the y-coordinates increasing from top to bottom.</span></span> <span data-ttu-id="bb3b4-105">Umístění počátek, relativně k obrazovce, budou lišit v závislosti na tom, jestli jsou zadání souřadnice obrazovky nebo klienta.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-105">The location of the origin, relative to the screen, will vary depending on whether you are specifying screen or client coordinates.</span></span>  
  
## <a name="screen-coordinates"></a><span data-ttu-id="bb3b4-106">Souřadnice obrazovky</span><span class="sxs-lookup"><span data-stu-id="bb3b4-106">Screen Coordinates</span></span>  
 <span data-ttu-id="bb3b4-107">Aplikace Windows Forms určuje pozici okna na obrazovce souřadnice obrazovky.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-107">A Windows Forms application specifies the position of a window on the screen in screen coordinates.</span></span> <span data-ttu-id="bb3b4-108">Souřadnice obrazovky pochází levého horního rohu obrazovky.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-108">For screen coordinates, the origin is the upper-left corner of the screen.</span></span> <span data-ttu-id="bb3b4-109">Úplné pozici okno je často popsán <xref:System.Drawing.Rectangle> struktura obsahující souřadnice obrazovky dva body, které definují rozích levém horním a pravém dolním rohu okna.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-109">The full position of a window is often described by a <xref:System.Drawing.Rectangle> structure containing the screen coordinates of two points that define the upper-left and lower-right corners of the window.</span></span>  
  
## <a name="client-coordinates"></a><span data-ttu-id="bb3b4-110">Souřadnice klienta</span><span class="sxs-lookup"><span data-stu-id="bb3b4-110">Client Coordinates</span></span>  
 <span data-ttu-id="bb3b4-111">Aplikace Windows Forms určuje pozici bodů ve formuláři nebo ovládacího prvku s použitím souřadnice klienta.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-111">A Windows Forms application specifies the position of points in a form or control using client coordinates.</span></span> <span data-ttu-id="bb3b4-112">Počátek souřadnice klienta je levém horním rohu klientské oblasti formuláře nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-112">The origin for client coordinates is the upper-left corner of the client area of the control or form.</span></span> <span data-ttu-id="bb3b4-113">Souřadnice klienta Ujistěte se, že aplikace můžete použít konzistentní souřadnic hodnoty při vykreslování ve formuláři nebo ovládací prvek, bez ohledu na pozici formuláře nebo ovládacího prvku na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-113">Client coordinates ensure that an application can use consistent coordinate values while drawing in a form or control, regardless of the position of the form or control on the screen.</span></span>  
  
 <span data-ttu-id="bb3b4-114">Dimenze klientské oblasti jsou také popsány podle <xref:System.Drawing.Rectangle> struktura, která obsahuje souřadnice klienta pro oblast.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-114">The dimensions of the client area are also described by a <xref:System.Drawing.Rectangle> structure that contains client coordinates for the area.</span></span> <span data-ttu-id="bb3b4-115">Ve všech případech je souřadnice levého horního obdélníku součástí klientské oblasti, zatímco je vyloučen souřadnice pravého dolního.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-115">In all cases, the upper-left coordinate of the rectangle is included in the client area, while the lower-right coordinate is excluded.</span></span> <span data-ttu-id="bb3b4-116">Grafické operace nezahrnují dolní a pravé hrany klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-116">Graphics operations do not include the right and lower edges of a client area.</span></span> <span data-ttu-id="bb3b4-117">Například <xref:System.Drawing.Graphics.FillRectangle%2A> metoda bude zaplnit vpravo a dolní hrany zadaný obdélníku, ale nebude obsahovat tyto okraje.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-117">For example the <xref:System.Drawing.Graphics.FillRectangle%2A> method will fill up to the right and lower edge of the specified rectangle, but will not include these edges.</span></span>  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a><span data-ttu-id="bb3b4-118">Mapování z jednoho typu souřadnice</span><span class="sxs-lookup"><span data-stu-id="bb3b4-118">Mapping From One Type of Coordinate to Another</span></span>  
 <span data-ttu-id="bb3b4-119">Potřebujete v některých případech mapování z souřadnice obrazovky na souřadnice klienta.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-119">Occasionally, you may need to map from screen coordinates to client coordinates.</span></span> <span data-ttu-id="bb3b4-120">Toho lze snadno dosáhnout pomocí <xref:System.Windows.Forms.Control.PointToClient%2A> a <xref:System.Windows.Forms.Control.PointToScreen%2A> metody, které jsou k dispozici v <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-120">You can easily accomplish this by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available in the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="bb3b4-121">Například <xref:System.Windows.Forms.Control.MousePosition%2A> vlastnost <xref:System.Windows.Forms.Control> je uvedený v souřadnice obrazovky, ale můžete chtít převést do souřadnice klienta.</span><span class="sxs-lookup"><span data-stu-id="bb3b4-121">For example, the <xref:System.Windows.Forms.Control.MousePosition%2A> property of <xref:System.Windows.Forms.Control> is reported in screen coordinates, but you may want to convert these to client coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb3b4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb3b4-122">See Also</span></span>  
 <xref:System.Windows.Forms.Control.PointToClient%2A>  
 <xref:System.Windows.Forms.Control.PointToScreen%2A>
