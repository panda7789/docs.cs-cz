---
title: "Vlastnosti v ovládacích prvcích Windows Forms, jež podporují pokyny pro usnadnění přístupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ca18b35b90b028054e68a0a14fecc819a6c20b9
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a><span data-ttu-id="a007d-102">Vlastnosti v ovládacích prvcích Windows Forms, jež podporují pokyny pro usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="a007d-102">Properties on Windows Forms Controls That Support Accessibility Guidelines</span></span>
<span data-ttu-id="a007d-103">Ovládací prvky na standardní sada nástrojů pro Windows Forms podporují řadu s pokyny, včetně vystavení fokus klávesnice a vystavení prvky obrazovky.</span><span class="sxs-lookup"><span data-stu-id="a007d-103">Controls on the standard toolbox for Windows Forms support many of the accessibility guidelines, including exposing the keyboard focus and exposing the screen elements.</span></span>  
  
## <a name="planning-ahead-for-accessibility"></a><span data-ttu-id="a007d-104">Plánování předem pro usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="a007d-104">Planning Ahead for Accessibility</span></span>  
 <span data-ttu-id="a007d-105">Ovládací prvky vlastnosti můžete použít pro podporu další pokyny pro usnadnění přístupu, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a007d-105">The controls' properties can be used to support other accessibility guidelines as shown in the following table.</span></span> <span data-ttu-id="a007d-106">Kromě toho používejte nabídky k poskytování přístupu k součástí programu.</span><span class="sxs-lookup"><span data-stu-id="a007d-106">Additionally, you should use menus to provide access to program features.</span></span>  
  
|<span data-ttu-id="a007d-107">Vlastnost ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="a007d-107">Control Property</span></span>|<span data-ttu-id="a007d-108">Důležité informace týkající se usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="a007d-108">Considerations for Accessibility</span></span>|  
|----------------------|--------------------------------------|  
|<span data-ttu-id="a007d-109">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="a007d-109">AccessibleDescription</span></span>|<span data-ttu-id="a007d-110">Popis se hlásí k usnadnění, jako jsou třeba čtečky obrazovky.</span><span class="sxs-lookup"><span data-stu-id="a007d-110">The description is reported to accessibility aids such as screen readers.</span></span> <span data-ttu-id="a007d-111">Usnadnění jsou specializované programy a zařízení, které pomáhají osoby s postižením efektivněji využívat počítače.</span><span class="sxs-lookup"><span data-stu-id="a007d-111">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span>|  
|<span data-ttu-id="a007d-112">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="a007d-112">AccessibleName</span></span>|<span data-ttu-id="a007d-113">Název, který bude ohlášena pomůcek pro usnadnění.</span><span class="sxs-lookup"><span data-stu-id="a007d-113">The name that will be reported to the accessibility aids.</span></span>|  
|<span data-ttu-id="a007d-114">AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="a007d-114">AccessibleRole</span></span>|<span data-ttu-id="a007d-115">Popisuje použití elementu v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a007d-115">Describes the use of the element in the user interface.</span></span>|  
|<span data-ttu-id="a007d-116">Pořadové číslo prvku</span><span class="sxs-lookup"><span data-stu-id="a007d-116">TabIndex</span></span>|<span data-ttu-id="a007d-117">Vytvoří rozumný navigační cesta pomocí formuláře.</span><span class="sxs-lookup"><span data-stu-id="a007d-117">Creates a sensible navigational path through the form.</span></span> <span data-ttu-id="a007d-118">Je důležité pro ovládací prvky bez vnitřní štítků, jako je například textová pole, jejich přidružené popisek bezprostředně je předcházet v pořadí.</span><span class="sxs-lookup"><span data-stu-id="a007d-118">It is important for controls without intrinsic labels, such as text boxes, to have their associated label immediately precede them in the tab order.</span></span>|  
|<span data-ttu-id="a007d-119">Text</span><span class="sxs-lookup"><span data-stu-id="a007d-119">Text</span></span>|<span data-ttu-id="a007d-120">Vytváření přístupových klíčů pomocí znaku "&".</span><span class="sxs-lookup"><span data-stu-id="a007d-120">Use the "&" character to create access keys.</span></span> <span data-ttu-id="a007d-121">Použití přístupových klíčů je součástí poskytnout zdokumentovaných klávesnice přístup k vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="a007d-121">Using access keys is part of providing documented keyboard access to features.</span></span>|  
|<span data-ttu-id="a007d-122">Velikost písma</span><span class="sxs-lookup"><span data-stu-id="a007d-122">Font Size</span></span>|<span data-ttu-id="a007d-123">Pokud není upravit velikost písma, pak je potřeba ho nastavit na 10 bodů nebo větší.</span><span class="sxs-lookup"><span data-stu-id="a007d-123">If the font size is not adjustable, then it should be set to 10 points or larger.</span></span> <span data-ttu-id="a007d-124">Jakmile je nastavena velikost písma formuláře, všechny ovládací prvky přidán do formuláře po tomto datu bude mít stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="a007d-124">Once the form's font size is set, all the controls added to the form thereafter will have the same size.</span></span>|  
|<span data-ttu-id="a007d-125">ForeColor</span><span class="sxs-lookup"><span data-stu-id="a007d-125">Forecolor</span></span>|<span data-ttu-id="a007d-126">Pokud je tato vlastnost nastavená na výchozí hodnoty, bude uživatelské předvolby barvu použít na formuláři.</span><span class="sxs-lookup"><span data-stu-id="a007d-126">If this property is set to the default, then the user's color preferences will be used on the form.</span></span>|  
|<span data-ttu-id="a007d-127">Barva pozadí</span><span class="sxs-lookup"><span data-stu-id="a007d-127">Backcolor</span></span>|<span data-ttu-id="a007d-128">Pokud je tato vlastnost nastavená na výchozí hodnoty, bude uživatelské předvolby barvu použít na formuláři.</span><span class="sxs-lookup"><span data-stu-id="a007d-128">If this property is set to the default, then the user's color preferences will be used on the form.</span></span>|  
|<span data-ttu-id="a007d-129">BackgroundImage</span><span class="sxs-lookup"><span data-stu-id="a007d-129">BackgroundImage</span></span>|<span data-ttu-id="a007d-130">Tuto vlastnost nezadáte tak čitelnost textu.</span><span class="sxs-lookup"><span data-stu-id="a007d-130">Leave this property blank to make text more readable.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a007d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="a007d-131">See Also</span></span>  
 [<span data-ttu-id="a007d-132">Návod: Vytvoření dostupné aplikace systému Windows</span><span class="sxs-lookup"><span data-stu-id="a007d-132">Walkthrough: Creating an Accessible Windows-based Application</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)
