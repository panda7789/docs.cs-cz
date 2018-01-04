---
title: "Použití grafických kontejnerů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 244f8e8a280369798daf12f8a61519826f937a4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-graphics-containers"></a><span data-ttu-id="118d4-102">Použití grafických kontejnerů</span><span class="sxs-lookup"><span data-stu-id="118d4-102">Using Graphics Containers</span></span>
<span data-ttu-id="118d4-103">A <xref:System.Drawing.Graphics> objekt poskytuje metody, jako například <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, a <xref:System.Drawing.Graphics.DrawString%2A> pro zobrazení vektoru obrázky, rastrové obrázky a text.</span><span class="sxs-lookup"><span data-stu-id="118d4-103">A <xref:System.Drawing.Graphics> object provides methods such as <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, and <xref:System.Drawing.Graphics.DrawString%2A> for displaying vector images, raster images, and text.</span></span> <span data-ttu-id="118d4-104">A <xref:System.Drawing.Graphics> objekt má také několik vlastností, které ovlivňují kvality a orientaci položky, které se mají vykreslovat.</span><span class="sxs-lookup"><span data-stu-id="118d4-104">A <xref:System.Drawing.Graphics> object also has several properties that influence the quality and orientation of the items that are drawn.</span></span> <span data-ttu-id="118d4-105">Například vlastnost režim vyhlazování Určuje, zda se použije vyhlazení u čar a křivek a vlastnost Světové transformace vliv pozice a oběh položek, které se mají vykreslovat.</span><span class="sxs-lookup"><span data-stu-id="118d4-105">For example, the smoothing mode property determines whether antialiasing is applied to lines and curves, and the world transformation property influences the position and rotation of the items that are drawn.</span></span>  
  
 <span data-ttu-id="118d4-106">A <xref:System.Drawing.Graphics> objekt je přidružený ke konkrétní zobrazení zařízení.</span><span class="sxs-lookup"><span data-stu-id="118d4-106">A <xref:System.Drawing.Graphics> object is associated with a particular display device.</span></span> <span data-ttu-id="118d4-107">Při použití <xref:System.Drawing.Graphics> objektu k vykreslení v okně <xref:System.Drawing.Graphics> objektu je taky přiřazený dané konkrétní okno.</span><span class="sxs-lookup"><span data-stu-id="118d4-107">When you use a <xref:System.Drawing.Graphics> object to draw in a window, the <xref:System.Drawing.Graphics> object is also associated with that particular window.</span></span>  
  
 <span data-ttu-id="118d4-108">A <xref:System.Drawing.Graphics> objekt si lze představit jako kontejner vzhledem k tomu, že obsahuje sadu vlastností, které ovlivňují kreslení a je propojen informace o zařízení.</span><span class="sxs-lookup"><span data-stu-id="118d4-108">A <xref:System.Drawing.Graphics> object can be thought of as a container because it holds a set of properties that influence drawing and it is linked to device-specific information.</span></span> <span data-ttu-id="118d4-109">Můžete vytvořit kontejner sekundární v rámci existující <xref:System.Drawing.Graphics> objekt voláním <xref:System.Drawing.Graphics.BeginContainer%2A> metoda této <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="118d4-109">You can create a secondary container within an existing <xref:System.Drawing.Graphics> object by calling the <xref:System.Drawing.Graphics.BeginContainer%2A> method of that <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="118d4-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="118d4-110">In This Section</span></span>  
 [<span data-ttu-id="118d4-111">Správa stavu grafického objektu</span><span class="sxs-lookup"><span data-stu-id="118d4-111">Managing the State of a Graphics Object</span></span>](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 <span data-ttu-id="118d4-112">Popisuje, jak spravovat nastavení kvality, výstřižek oblasti a transformace z <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="118d4-112">Describes how manage the quality settings, clipping area and transformations of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [<span data-ttu-id="118d4-113">Použití vnořených grafických kontejnerů</span><span class="sxs-lookup"><span data-stu-id="118d4-113">Using Nested Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 <span data-ttu-id="118d4-114">Ukazuje, jak použít k řízení stavu kontejnery <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="118d4-114">Shows how to use containers to control the state of the <xref:System.Drawing.Graphics> object.</span></span>
