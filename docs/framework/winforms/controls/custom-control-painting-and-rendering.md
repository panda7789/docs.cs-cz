---
title: Malování a vykreslování vlastního ovládacího prvku
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: ec9002ffa4a7e2c82f59d52344764a01afe4c568
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722136"
---
# <a name="custom-control-painting-and-rendering"></a><span data-ttu-id="247ce-102">Malování a vykreslování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="247ce-102">Custom Control Painting and Rendering</span></span>
<span data-ttu-id="247ce-103">Vlastní vykreslování ovládacích prvků je jednou z mnoha složité úkoly snadné rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="247ce-103">Custom painting of controls is one of the many complicated tasks made easy by the .NET Framework.</span></span> <span data-ttu-id="247ce-104">Při vytváření vlastního ovládacího prvku, máte celou řadu možností týkající se vzhled grafického ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="247ce-104">When authoring a custom control, you have many options regarding your control's graphical appearance.</span></span> <span data-ttu-id="247ce-105">Vytváříte-li ovládací prvek, který dědí z `Control`, je nutné zadat kód, který umožňuje ovládacího prvku k vykreslení jeho grafickou reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="247ce-105">If you are authoring a control that inherits from the `Control`, you must provide code that allows your control to render its graphical representation.</span></span> <span data-ttu-id="247ce-106">Pokud vytváříte uživatelský ovládací prvek děděním z `UserControl`, nebo dědí z jednoho z ovládacích prvků Windows Forms, mohou přepsat standardní grafické vyjádření a poskytují grafického kódu.</span><span class="sxs-lookup"><span data-stu-id="247ce-106">If you are creating a user control by inheriting from the `UserControl`, or are inheriting from one of the Windows Forms controls, you may override the standard graphical representation and provide your own graphics code.</span></span> <span data-ttu-id="247ce-107">Pokud chcete poskytnout vlastní vykreslování pro základní ovládací prvky `UserControl` vytváříte, vaše možnosti omezenější, ale přesto umožňuje širokou škálu grafické možnosti pro ovládací prvky a aplikace.</span><span class="sxs-lookup"><span data-stu-id="247ce-107">If you want to provide custom rendering for the constituent controls of a `UserControl` you are authoring, your options become more limited, but still allow a wide range of graphical possibilities for your controls and applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="247ce-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="247ce-108">In This Section</span></span>  
 [<span data-ttu-id="247ce-109">Vykreslení ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="247ce-109">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)  
 <span data-ttu-id="247ce-110">Ukazuje, jak aplikaci logiky, která se zobrazí ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="247ce-110">Shows how to program the logic that displays a control.</span></span>  
  
 [<span data-ttu-id="247ce-111">Ovládací prvky vykreslované uživatelem</span><span class="sxs-lookup"><span data-stu-id="247ce-111">User-Drawn Controls</span></span>](user-drawn-controls.md)  
 <span data-ttu-id="247ce-112">Poskytuje přehled o postup psaní a přepsáním kód pro vykreslování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="247ce-112">Gives an overview of the steps involved in writing and overriding rendering code for your control.</span></span>  
  
 [<span data-ttu-id="247ce-113">Základní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="247ce-113">Constituent Controls</span></span>](constituent-controls.md)  
 <span data-ttu-id="247ce-114">Popisuje, jak implementovat vlastní vykreslování kód pro základních ovládacích prvků ve formulářích a uživatelských ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="247ce-114">Describes how to implement custom rendering code for constituent controls in your user controls and forms.</span></span>  
  
 [<span data-ttu-id="247ce-115">Postupy: Skrytí vlastního ovládacího prvku za běhu</span><span class="sxs-lookup"><span data-stu-id="247ce-115">How to: Make Your Control Invisible at Run Time</span></span>](how-to-make-your-control-invisible-at-run-time.md)  
 <span data-ttu-id="247ce-116">Ukazuje způsob použití <xref:System.Windows.Forms.Control.Visible%2A> vlastnost skrytí a zobrazení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="247ce-116">Shows how to use the <xref:System.Windows.Forms.Control.Visible%2A> property to hide and show a control.</span></span>  
  
 [<span data-ttu-id="247ce-117">Postupy: Zadejte svůj ovládací prvek průhledné pozadí</span><span class="sxs-lookup"><span data-stu-id="247ce-117">How to: Give Your Control a Transparent Background</span></span>](how-to-give-your-control-a-transparent-background.md)  
 <span data-ttu-id="247ce-118">Ukazuje způsob použití <xref:System.Windows.Forms.Control.SetStyle%2A> metodu pro vytvoření barvu pozadí, který je neprůhledný, průhledného nebo částečně.</span><span class="sxs-lookup"><span data-stu-id="247ce-118">Shows how to use the <xref:System.Windows.Forms.Control.SetStyle%2A> method to create a background color that is opaque, transparent, or partially transparent.</span></span>  
  
 [<span data-ttu-id="247ce-119">Vykreslování ovládacích prvků s vizuálními styly</span><span class="sxs-lookup"><span data-stu-id="247ce-119">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)  
 <span data-ttu-id="247ce-120">Ukazuje, jak pro vykreslení ovládacích prvků pomocí vizuálních stylů v operačních systémech, které je podporují.</span><span class="sxs-lookup"><span data-stu-id="247ce-120">Shows how to render controls using visual styles in operating systems that support them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="247ce-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="247ce-121">Reference</span></span>  
 <xref:System.Windows.Forms.Control>  
 <span data-ttu-id="247ce-122">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="247ce-122">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="247ce-123">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="247ce-123">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <span data-ttu-id="247ce-124">Popisuje tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="247ce-124">Describes this method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="247ce-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="247ce-125">Related Sections</span></span>  
 [<span data-ttu-id="247ce-126">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="247ce-126">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)  
 <span data-ttu-id="247ce-127">Zavádí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafické funkce z Visual Studio perspektivy a poskytuje odkazy na další informace.</span><span class="sxs-lookup"><span data-stu-id="247ce-127">Introduces [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] graphics functionality from a Visual Studio perspective and gives links to more information.</span></span>  
  
 [<span data-ttu-id="247ce-128">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="247ce-128">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="247ce-129">Popisuje typy vlastních ovládacích prvků, které můžete vytvářet.</span><span class="sxs-lookup"><span data-stu-id="247ce-129">Describes the kinds of custom controls you can author.</span></span>
