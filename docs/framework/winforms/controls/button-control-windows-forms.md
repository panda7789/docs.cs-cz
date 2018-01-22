---
title: "Ovládací prvek Tlačítko (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons
- Button control [Windows Forms]
ms.assetid: d38bc40c-8040-4f19-9e88-2c665b0ab80b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4f9720f26458f3dd9cb2411d123fa830b20f3fd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="button-control-windows-forms"></a><span data-ttu-id="e6f3e-102">Ovládací prvek Tlačítko (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e6f3e-102">Button Control (Windows Forms)</span></span>
<span data-ttu-id="e6f3e-103">Windows Forms `Button` řízení umožňuje uživateli klikněte na něj k provedení akce.</span><span class="sxs-lookup"><span data-stu-id="e6f3e-103">The Windows Forms `Button` control allows the user to click it to perform an action.</span></span> <span data-ttu-id="e6f3e-104">`Button` Ovládací prvek může zobrazit textu a obrázků.</span><span class="sxs-lookup"><span data-stu-id="e6f3e-104">The `Button` control can display both text and images.</span></span> <span data-ttu-id="e6f3e-105">Při kliknutí na tlačítko efekt stisknuté a vydání.</span><span class="sxs-lookup"><span data-stu-id="e6f3e-105">When the button is clicked, it looks as if it is being pushed in and released.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e6f3e-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e6f3e-106">In This Section</span></span>  
 [<span data-ttu-id="e6f3e-107">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="e6f3e-107">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 <span data-ttu-id="e6f3e-108">Vysvětluje, co je tento ovládací prvek a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e6f3e-108">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="e6f3e-109">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6f3e-109">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 <span data-ttu-id="e6f3e-110">Vysvětluje nejzákladnější použití tlačítko ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="e6f3e-110">Explains the most basic use of a button on a Windows Form.</span></span>  
  
 [<span data-ttu-id="e6f3e-111">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout</span><span class="sxs-lookup"><span data-stu-id="e6f3e-111">How to: Designate a Windows Forms Button as the Accept Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 <span data-ttu-id="e6f3e-112">Vysvětluje, jak určit `Button` ovládacího prvku tlačítko Přijmout, také známé jako výchozího tlačítka.</span><span class="sxs-lookup"><span data-stu-id="e6f3e-112">Explains how to designate a `Button` control to be the accept button, also known as the default button.</span></span>  
  
 [<span data-ttu-id="e6f3e-113">Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit</span><span class="sxs-lookup"><span data-stu-id="e6f3e-113">How to: Designate a Windows Forms Button as the Cancel Button</span></span>](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)  
 <span data-ttu-id="e6f3e-114">Vysvětluje, jak určit `Button` ovládacího prvku tlačítko Zrušit, které po kliknutí na vždy, když uživatel stisknutím klávesy ESC.</span><span class="sxs-lookup"><span data-stu-id="e6f3e-114">Explains how to designate a `Button` control to be the cancel button, which is clicked whenever the user presses the ESC key.</span></span>  
  
 [<span data-ttu-id="e6f3e-115">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="e6f3e-115">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 <span data-ttu-id="e6f3e-116">Uvádí metody výběru tlačítka.</span><span class="sxs-lookup"><span data-stu-id="e6f3e-116">Lists methods of selecting a button.</span></span>  
  
 <span data-ttu-id="e6f3e-117">Viz také [postupy: určení tlačítka Windows Forms na přijmout tlačítko pomocí návrháře](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md) a [postupy: určení tlačítka Windows Forms ke zrušení tlačítko pomocí návrháře](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="e6f3e-117">Also see [How to: Designate a Windows Forms Button as the Accept Button Using the Designer](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md) and [How to: Designate a Windows Forms Button as the Cancel Button Using the Designer](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e6f3e-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="e6f3e-118">Reference</span></span>  
 <span data-ttu-id="e6f3e-119"><xref:System.Windows.Forms.Button>– Třída</span><span class="sxs-lookup"><span data-stu-id="e6f3e-119"><xref:System.Windows.Forms.Button> class</span></span>  
 <span data-ttu-id="e6f3e-120">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="e6f3e-120">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e6f3e-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e6f3e-121">Related Sections</span></span>  
 [<span data-ttu-id="e6f3e-122">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6f3e-122">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="e6f3e-123">Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.</span><span class="sxs-lookup"><span data-stu-id="e6f3e-123">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 <span data-ttu-id="e6f3e-124">Viz také [uživatelský vstup do dialogových oken](http://msdn.microsoft.com/library/63ad8645-6842-45e8-b215-73f778e29a55) a [postup: zavřít dialogová okna a zachovat uživatelský vstup](http://msdn.microsoft.com/library/9e118fad-3bf4-4f70-a3de-a0cda2b0229d).</span><span class="sxs-lookup"><span data-stu-id="e6f3e-124">Also see [User Input to Dialog Boxes](http://msdn.microsoft.com/library/63ad8645-6842-45e8-b215-73f778e29a55) and [How to: Close Dialog Boxes and Retain User Input](http://msdn.microsoft.com/library/9e118fad-3bf4-4f70-a3de-a0cda2b0229d).</span></span>
