---
title: "Malování a vykreslování vlastního ovládacího prvku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: babf3d235f4cca61ad6d0e5fdc4e6b6146c7d060
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="custom-control-painting-and-rendering"></a><span data-ttu-id="85d55-102">Malování a vykreslování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="85d55-102">Custom Control Painting and Rendering</span></span>
<span data-ttu-id="85d55-103">Vlastní vykreslování ovládacích prvků je jedním z mnoha složitá úloha, umožněno pomocí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="85d55-103">Custom painting of controls is one of the many complicated tasks made easy by the .NET Framework.</span></span> <span data-ttu-id="85d55-104">Při vytváření vlastního ovládacího prvku, máte mnoho možnosti týkající se grafické vzhledu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="85d55-104">When authoring a custom control, you have many options regarding your control's graphical appearance.</span></span> <span data-ttu-id="85d55-105">Vytváříte-li ovládací prvek, který dědí z `Control`, je nutné zadat kód, který umožňuje vaší řídit k vykreslení jeho grafické reprezentace.</span><span class="sxs-lookup"><span data-stu-id="85d55-105">If you are authoring a control that inherits from the `Control`, you must provide code that allows your control to render its graphical representation.</span></span> <span data-ttu-id="85d55-106">Pokud vytváříte uživatelský ovládací prvek dědění ze `UserControl`, nebo se dědí z jednoho z ovládacích prvků Windows Forms, můžete přepsat standardní grafické vyjádření a zadejte vlastní kód grafiky.</span><span class="sxs-lookup"><span data-stu-id="85d55-106">If you are creating a user control by inheriting from the `UserControl`, or are inheriting from one of the Windows Forms controls, you may override the standard graphical representation and provide your own graphics code.</span></span> <span data-ttu-id="85d55-107">Pokud chcete zadat vlastní vykreslení pro základní ovládací prvky systému `UserControl` vytváříte, možnosti omezenější, ale stále povolit širokou škálu grafické možnosti pro ovládací prvky a aplikace.</span><span class="sxs-lookup"><span data-stu-id="85d55-107">If you want to provide custom rendering for the constituent controls of a `UserControl` you are authoring, your options become more limited, but still allow a wide range of graphical possibilities for your controls and applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85d55-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="85d55-108">In This Section</span></span>  
 [<span data-ttu-id="85d55-109">Vykreslování ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="85d55-109">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 <span data-ttu-id="85d55-110">Ukazuje, jak program logiky, která zobrazuje ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="85d55-110">Shows how to program the logic that displays a control.</span></span>  
  
 [<span data-ttu-id="85d55-111">Ovládací prvky vykreslované uživatelem</span><span class="sxs-lookup"><span data-stu-id="85d55-111">User-Drawn Controls</span></span>](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 <span data-ttu-id="85d55-112">Poskytuje přehled jednotlivými kroky při psaní a přepsání kód vykreslování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="85d55-112">Gives an overview of the steps involved in writing and overriding rendering code for your control.</span></span>  
  
 [<span data-ttu-id="85d55-113">Základní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="85d55-113">Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 <span data-ttu-id="85d55-114">Popisuje, jak implementovat vlastní vykreslení kód pro základních ovládacích prvků ve formulářích a uživatelské ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="85d55-114">Describes how to implement custom rendering code for constituent controls in your user controls and forms.</span></span>  
  
 [<span data-ttu-id="85d55-115">Postupy: skrytí vlastního ovládacího prvku za běhu</span><span class="sxs-lookup"><span data-stu-id="85d55-115">How to: Make Your Control Invisible at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 <span data-ttu-id="85d55-116">Ukazuje, jak používat <xref:System.Windows.Forms.Control.Visible%2A> vlastnost skrýt a zobrazit ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="85d55-116">Shows how to use the <xref:System.Windows.Forms.Control.Visible%2A> property to hide and show a control.</span></span>  
  
 [<span data-ttu-id="85d55-117">Postupy: poskytnout vlastní ovládací prvek průhledné pozadí</span><span class="sxs-lookup"><span data-stu-id="85d55-117">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 <span data-ttu-id="85d55-118">Ukazuje, jak používat <xref:System.Windows.Forms.Control.SetStyle%2A> metodu pro vytvoření barvu pozadí, který je plné krytí, transparentní nebo částečně transparentní.</span><span class="sxs-lookup"><span data-stu-id="85d55-118">Shows how to use the <xref:System.Windows.Forms.Control.SetStyle%2A> method to create a background color that is opaque, transparent, or partially transparent.</span></span>  
  
 [<span data-ttu-id="85d55-119">Vykreslení ovládacích prvků s vizuálními styly</span><span class="sxs-lookup"><span data-stu-id="85d55-119">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 <span data-ttu-id="85d55-120">Ukazuje, jak k vykreslení ovládacích prvků pomocí vizuální styly v operačních systémech, které je podporují.</span><span class="sxs-lookup"><span data-stu-id="85d55-120">Shows how to render controls using visual styles in operating systems that support them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="85d55-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="85d55-121">Reference</span></span>  
 <xref:System.Windows.Forms.Control>  
 <span data-ttu-id="85d55-122">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="85d55-122">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="85d55-123">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="85d55-123">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <span data-ttu-id="85d55-124">Popisuje tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="85d55-124">Describes this method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="85d55-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="85d55-125">Related Sections</span></span>  
 [<span data-ttu-id="85d55-126">Postupy: vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="85d55-126">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 <span data-ttu-id="85d55-127">Představuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkce grafiky sady Visual Studio perspektivy a poskytuje odkazy na další informace.</span><span class="sxs-lookup"><span data-stu-id="85d55-127">Introduces [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] graphics functionality from a Visual Studio perspective and gives links to more information.</span></span>  
  
 [<span data-ttu-id="85d55-128">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="85d55-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="85d55-129">Popisuje typy vlastních ovládacích prvků, které můžete vytvářet.</span><span class="sxs-lookup"><span data-stu-id="85d55-129">Describes the kinds of custom controls you can author.</span></span>
