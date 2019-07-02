---
title: Malování a vykreslování vlastního ovládacího prvku
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: 14abac5678bfffa3cdb61307fd3cb54681c82a99
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506093"
---
# <a name="custom-control-painting-and-rendering"></a><span data-ttu-id="d262e-102">Malování a vykreslování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d262e-102">Custom Control Painting and Rendering</span></span>
<span data-ttu-id="d262e-103">Vlastní vykreslování ovládacích prvků je jednou z mnoha složité úkoly snadné rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d262e-103">Custom painting of controls is one of the many complicated tasks made easy by the .NET Framework.</span></span> <span data-ttu-id="d262e-104">Při vytváření vlastního ovládacího prvku, máte celou řadu možností týkající se vzhled grafického ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d262e-104">When authoring a custom control, you have many options regarding your control's graphical appearance.</span></span> <span data-ttu-id="d262e-105">Vytváříte-li ovládací prvek, který dědí z `Control`, je nutné zadat kód, který umožňuje ovládacího prvku k vykreslení jeho grafickou reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="d262e-105">If you are authoring a control that inherits from the `Control`, you must provide code that allows your control to render its graphical representation.</span></span> <span data-ttu-id="d262e-106">Pokud vytváříte uživatelský ovládací prvek děděním z `UserControl`, nebo dědí z jednoho z ovládacích prvků Windows Forms, mohou přepsat standardní grafické vyjádření a poskytují grafického kódu.</span><span class="sxs-lookup"><span data-stu-id="d262e-106">If you are creating a user control by inheriting from the `UserControl`, or are inheriting from one of the Windows Forms controls, you may override the standard graphical representation and provide your own graphics code.</span></span> <span data-ttu-id="d262e-107">Pokud chcete poskytnout vlastní vykreslování pro základní ovládací prvky `UserControl` vytváříte, vaše možnosti omezenější, ale přesto umožňuje širokou škálu grafické možnosti pro ovládací prvky a aplikace.</span><span class="sxs-lookup"><span data-stu-id="d262e-107">If you want to provide custom rendering for the constituent controls of a `UserControl` you are authoring, your options become more limited, but still allow a wide range of graphical possibilities for your controls and applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d262e-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d262e-108">In This Section</span></span>  
 [<span data-ttu-id="d262e-109">Vykreslení ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d262e-109">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)  
 <span data-ttu-id="d262e-110">Ukazuje, jak aplikaci logiky, která se zobrazí ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="d262e-110">Shows how to program the logic that displays a control.</span></span>  
  
 [<span data-ttu-id="d262e-111">Ovládací prvky vykreslované uživatelem</span><span class="sxs-lookup"><span data-stu-id="d262e-111">User-Drawn Controls</span></span>](user-drawn-controls.md)  
 <span data-ttu-id="d262e-112">Poskytuje přehled o postup psaní a přepsáním kód pro vykreslování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d262e-112">Gives an overview of the steps involved in writing and overriding rendering code for your control.</span></span>  
  
 [<span data-ttu-id="d262e-113">Základní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="d262e-113">Constituent Controls</span></span>](constituent-controls.md)  
 <span data-ttu-id="d262e-114">Popisuje, jak implementovat vlastní vykreslování kód pro základních ovládacích prvků ve formulářích a uživatelských ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="d262e-114">Describes how to implement custom rendering code for constituent controls in your user controls and forms.</span></span>  
  
 [<span data-ttu-id="d262e-115">Postupy: Skrytí vlastního ovládacího prvku za běhu</span><span class="sxs-lookup"><span data-stu-id="d262e-115">How to: Make Your Control Invisible at Run Time</span></span>](how-to-make-your-control-invisible-at-run-time.md)  
 <span data-ttu-id="d262e-116">Ukazuje způsob použití <xref:System.Windows.Forms.Control.Visible%2A> vlastnost skrytí a zobrazení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d262e-116">Shows how to use the <xref:System.Windows.Forms.Control.Visible%2A> property to hide and show a control.</span></span>  
  
 [<span data-ttu-id="d262e-117">Postupy: Zadejte svůj ovládací prvek průhledné pozadí</span><span class="sxs-lookup"><span data-stu-id="d262e-117">How to: Give Your Control a Transparent Background</span></span>](how-to-give-your-control-a-transparent-background.md)  
 <span data-ttu-id="d262e-118">Ukazuje způsob použití <xref:System.Windows.Forms.Control.SetStyle%2A> metodu pro vytvoření barvu pozadí, který je neprůhledný, průhledného nebo částečně.</span><span class="sxs-lookup"><span data-stu-id="d262e-118">Shows how to use the <xref:System.Windows.Forms.Control.SetStyle%2A> method to create a background color that is opaque, transparent, or partially transparent.</span></span>  
  
 [<span data-ttu-id="d262e-119">Vykreslování ovládacích prvků s vizuálními styly</span><span class="sxs-lookup"><span data-stu-id="d262e-119">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)  
 <span data-ttu-id="d262e-120">Ukazuje, jak pro vykreslení ovládacích prvků pomocí vizuálních stylů v operačních systémech, které je podporují.</span><span class="sxs-lookup"><span data-stu-id="d262e-120">Shows how to render controls using visual styles in operating systems that support them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d262e-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d262e-121">Reference</span></span>  
 <xref:System.Windows.Forms.Control>  
 <span data-ttu-id="d262e-122">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="d262e-122">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="d262e-123">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="d262e-123">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <span data-ttu-id="d262e-124">Popisuje tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="d262e-124">Describes this method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d262e-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d262e-125">Related Sections</span></span>  
 [<span data-ttu-id="d262e-126">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="d262e-126">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)  
 <span data-ttu-id="d262e-127">Představuje grafické funkce rozhraní GDI + z hlediska sady Visual Studio a nabízí odkazy na další informace.</span><span class="sxs-lookup"><span data-stu-id="d262e-127">Introduces GDI+ graphics functionality from a Visual Studio perspective and gives links to more information.</span></span>  
  
 [<span data-ttu-id="d262e-128">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="d262e-128">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="d262e-129">Popisuje typy vlastních ovládacích prvků, které můžete vytvářet.</span><span class="sxs-lookup"><span data-stu-id="d262e-129">Describes the kinds of custom controls you can author.</span></span>
