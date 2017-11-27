---
title: "DomainUpDown – ovládací prvek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 37cec82876edadfed5cda338ca12775ad19ae732
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="domainupdown-control-windows-forms"></a><span data-ttu-id="f8f48-102">DomainUpDown – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f8f48-102">DomainUpDown Control (Windows Forms)</span></span>
<span data-ttu-id="f8f48-103">Windows Forms <xref:System.Windows.Forms.DomainUpDown> řízení vypadá jako kombinace textového pole a pár tlačítka pro přesun nahoru nebo dolů v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f8f48-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control looks like a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="f8f48-104">Ovládací prvek zobrazí a nastaví textový řetězec ze seznamu voleb.</span><span class="sxs-lookup"><span data-stu-id="f8f48-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="f8f48-105">Uživatele můžete vybrat řetězec, klikněte na tlačítka pro přesouvání v seznamu nahoru a dolů, stisknutím klávesy se šipkami nahoru a dolů nebo zadáním řetězec, který odpovídá položku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f8f48-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="f8f48-106">Je možné použití tohoto ovládacího prvku pro výběr položek z abecedně seřazený seznam názvů.</span><span class="sxs-lookup"><span data-stu-id="f8f48-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span> <span data-ttu-id="f8f48-107">(Seřadíte seznam nastavit <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> vlastnost `true`.) Funkce tohoto ovládacího prvku je velmi podobný pole se seznamem nebo pole se seznamem, ale zabírají velmi málo místa.</span><span class="sxs-lookup"><span data-stu-id="f8f48-107">(To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.) The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
 <span data-ttu-id="f8f48-108">Klíčové vlastnosti ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, a <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8f48-108">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="f8f48-109"><xref:System.Windows.Forms.DomainUpDown.Items%2A> Vlastnost obsahuje seznam objektů, jejichž hodnoty text se zobrazí v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="f8f48-109">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="f8f48-110">Pokud <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> je nastaven na `false`, ovládacího prvku automaticky dokončení text, že uživatel nezadá a odpovídá hodnotě v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f8f48-110">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="f8f48-111">Pokud <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> je nastaven na `true`, posouvání za poslední položky se dostanete na první položku v seznamu a naopak.</span><span class="sxs-lookup"><span data-stu-id="f8f48-111">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="f8f48-112">Klíče metody ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> a <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8f48-112">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="f8f48-113">Tento ovládací prvek zobrazí pouze textové řetězce.</span><span class="sxs-lookup"><span data-stu-id="f8f48-113">This control displays only text strings.</span></span> <span data-ttu-id="f8f48-114">Pokud chcete ovládacího prvku, který zobrazí číselné hodnoty, použijte <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f8f48-114">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="f8f48-115">Další informace najdete v tématu [NumericUpDown – ovládací prvek](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .</span><span class="sxs-lookup"><span data-stu-id="f8f48-115">For more information, see [NumericUpDown Control](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8f48-116">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f8f48-116">In This Section</span></span>  
 [<span data-ttu-id="f8f48-117">Přehled ovládacího prvku DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="f8f48-117">DomainUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 <span data-ttu-id="f8f48-118">Představuje obecné koncepty <xref:System.Windows.Forms.DomainUpDown> řízení, které umožňuje uživatelům procházet a vyberte ze seznamu textové řetězce.</span><span class="sxs-lookup"><span data-stu-id="f8f48-118">Introduces the general concepts of the <xref:System.Windows.Forms.DomainUpDown> control, which allows users to browse through and select from a list of text strings.</span></span>  
  
 [<span data-ttu-id="f8f48-119">Postupy: Přidání položky do Windows Forms DomainUpDown – ovládací prvky prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="f8f48-119">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 <span data-ttu-id="f8f48-120">Popisuje, jak zadat textového řetězce <xref:System.Windows.Forms.DomainUpDown> by měl zobrazit ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f8f48-120">Describes how to specify the text strings the <xref:System.Windows.Forms.DomainUpDown> control should display.</span></span>  
  
 [<span data-ttu-id="f8f48-121">Postupy: odebrání položek z rozhraní Windows Forms DomainUpDown – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="f8f48-121">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 <span data-ttu-id="f8f48-122">Popisuje postup odstranění položek z <xref:System.Windows.Forms.DomainUpDown> ovládací prvek v kódu.</span><span class="sxs-lookup"><span data-stu-id="f8f48-122">Describes how to delete items from the <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f8f48-123">Odkaz</span><span class="sxs-lookup"><span data-stu-id="f8f48-123">Reference</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <span data-ttu-id="f8f48-124">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="f8f48-124">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 <span data-ttu-id="f8f48-125">Tato třída popisuje a obsahuje odkazy na všechny její členy...</span><span class="sxs-lookup"><span data-stu-id="f8f48-125">Describes this class and has links to all its members..</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f8f48-126">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f8f48-126">Related Sections</span></span>  
 [<span data-ttu-id="f8f48-127">Ovládací prvky, které můžete použít v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f8f48-127">Controls You Can Use On Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="f8f48-128">Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.</span><span class="sxs-lookup"><span data-stu-id="f8f48-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
