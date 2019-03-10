---
title: Použití grafických kontejnerů
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
ms.openlocfilehash: cfad7254057a31ea8268784cd4b6849850f3e2aa
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704462"
---
# <a name="using-graphics-containers"></a><span data-ttu-id="6e263-102">Použití grafických kontejnerů</span><span class="sxs-lookup"><span data-stu-id="6e263-102">Using Graphics Containers</span></span>
<span data-ttu-id="6e263-103">A <xref:System.Drawing.Graphics> objekt, který poskytuje metody, jako <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, a <xref:System.Drawing.Graphics.DrawString%2A> pro zobrazení vektorové obrázky, rastrové obrázky a text.</span><span class="sxs-lookup"><span data-stu-id="6e263-103">A <xref:System.Drawing.Graphics> object provides methods such as <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, and <xref:System.Drawing.Graphics.DrawString%2A> for displaying vector images, raster images, and text.</span></span> <span data-ttu-id="6e263-104">A <xref:System.Drawing.Graphics> objekt má také několik vlastností, které ovlivňují kvality a orientaci ovládacího prvku položek, které jsou zpracovány.</span><span class="sxs-lookup"><span data-stu-id="6e263-104">A <xref:System.Drawing.Graphics> object also has several properties that influence the quality and orientation of the items that are drawn.</span></span> <span data-ttu-id="6e263-105">Například vlastnost vyhlazování režimu určuje, zda použití vyhlazení u čar a křivek a vlastnost transformace světa ovlivňuje umístění a otočení položek, které jsou zpracovány.</span><span class="sxs-lookup"><span data-stu-id="6e263-105">For example, the smoothing mode property determines whether antialiasing is applied to lines and curves, and the world transformation property influences the position and rotation of the items that are drawn.</span></span>  
  
 <span data-ttu-id="6e263-106">A <xref:System.Drawing.Graphics> objekt je přidružený konkrétní zobrazovací zařízení.</span><span class="sxs-lookup"><span data-stu-id="6e263-106">A <xref:System.Drawing.Graphics> object is associated with a particular display device.</span></span> <span data-ttu-id="6e263-107">Při použití <xref:System.Drawing.Graphics> objekt nakreslete v okně <xref:System.Drawing.Graphics> objektu je taky přiřazený k této konkrétní okno.</span><span class="sxs-lookup"><span data-stu-id="6e263-107">When you use a <xref:System.Drawing.Graphics> object to draw in a window, the <xref:System.Drawing.Graphics> object is also associated with that particular window.</span></span>  
  
 <span data-ttu-id="6e263-108">A <xref:System.Drawing.Graphics> objektu můžete představit jako kontejner protože obsahuje sadu vlastností, které ovlivňují kreslení a je propojen informace specifické pro zařízení.</span><span class="sxs-lookup"><span data-stu-id="6e263-108">A <xref:System.Drawing.Graphics> object can be thought of as a container because it holds a set of properties that influence drawing and it is linked to device-specific information.</span></span> <span data-ttu-id="6e263-109">Můžete vytvořit kontejner sekundární v existující <xref:System.Drawing.Graphics> objektu voláním <xref:System.Drawing.Graphics.BeginContainer%2A> metodu, která <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="6e263-109">You can create a secondary container within an existing <xref:System.Drawing.Graphics> object by calling the <xref:System.Drawing.Graphics.BeginContainer%2A> method of that <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e263-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6e263-110">In This Section</span></span>  
 [<span data-ttu-id="6e263-111">Správa stavu grafického objektu</span><span class="sxs-lookup"><span data-stu-id="6e263-111">Managing the State of a Graphics Object</span></span>](managing-the-state-of-a-graphics-object.md)  
 <span data-ttu-id="6e263-112">Popisuje, jak spravovat nastavení kvality, výstřižek oblasti a transformace <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="6e263-112">Describes how manage the quality settings, clipping area and transformations of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [<span data-ttu-id="6e263-113">Použití vnořených grafických kontejnerů</span><span class="sxs-lookup"><span data-stu-id="6e263-113">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)  
 <span data-ttu-id="6e263-114">Ukazuje, jak používat kontejnery k řízení stavu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="6e263-114">Shows how to use containers to control the state of the <xref:System.Drawing.Graphics> object.</span></span>
