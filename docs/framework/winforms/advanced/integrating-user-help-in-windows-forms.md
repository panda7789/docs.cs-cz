---
title: "Integrace uživatelské nápovědy do formulářů Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9563ce0ca95a728cc1a9aaa219fbc9fea2cd7153
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="2c9c7-102">Integrace uživatelské nápovědy do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="2c9c7-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="2c9c7-103">Základní, ale často přehlíženým aspekt vytváření aplikace pro systém Windows je systém nápovědy, protože se jedná, kde uživatelé zapnout pro pomoc časů záměny.</span><span class="sxs-lookup"><span data-stu-id="2c9c7-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="2c9c7-104">Windows Forms – podpora dva různé typy nápovědy, každý poskytované [HelpProvider – komponenta](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2c9c7-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="2c9c7-105">První zahrnuje soubor nápovědy HTML nebo 1 Nápověda HTML přejdete na příkaz uživatele. *x* nebo větší formát.</span><span class="sxs-lookup"><span data-stu-id="2c9c7-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="2c9c7-106">Druhý můžete zobrazit stručný "Co je to"-Zadejte nápovědy na jednotlivých ovládacích prvků; To je užitečné zejména v dialogových oknech.</span><span class="sxs-lookup"><span data-stu-id="2c9c7-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="2c9c7-107">Oba typy nápovědy lze použít na stejném tvaru.</span><span class="sxs-lookup"><span data-stu-id="2c9c7-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="2c9c7-108">Kromě toho [ToolTip – komponenta](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md) lze jednotlivé pomoci pro ovládací prvky na formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="2c9c7-108">Additionally, the [ToolTip Component](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c9c7-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2c9c7-109">In This Section</span></span>  
 [<span data-ttu-id="2c9c7-110">Postupy: Poskytnutí nápovědy v aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="2c9c7-110">How to: Provide Help in a Windows Application</span></span>](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="2c9c7-111">Vysvětluje, jak používat `HelpProvider` součást propojení ovládacích prvků do souborů v systému nápovědy.</span><span class="sxs-lookup"><span data-stu-id="2c9c7-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="2c9c7-112">Postupy: Zobrazení místní nápovědy</span><span class="sxs-lookup"><span data-stu-id="2c9c7-112">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 <span data-ttu-id="2c9c7-113">Vysvětluje, jak používat `HelpProvider` součást zobrazit automaticky otevírané okno nápovědu v rozhraní Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2c9c7-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="2c9c7-114">Nápověda ovládacího prvku pomocí ToolTips</span><span class="sxs-lookup"><span data-stu-id="2c9c7-114">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 <span data-ttu-id="2c9c7-115">Popisuje použití `ToolTip` součást zobrazit nápovědu specifické pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="2c9c7-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2c9c7-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2c9c7-116">Related Sections</span></span>  
 [<span data-ttu-id="2c9c7-117">Komponenta HelpProvider</span><span class="sxs-lookup"><span data-stu-id="2c9c7-117">HelpProvider Component</span></span>](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="2c9c7-118">Vysvětluje základy `HelpProvider` součásti.</span><span class="sxs-lookup"><span data-stu-id="2c9c7-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="2c9c7-119">Komponenta ToolTip</span><span class="sxs-lookup"><span data-stu-id="2c9c7-119">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="2c9c7-120">Vysvětluje základy `ToolTip` součásti.</span><span class="sxs-lookup"><span data-stu-id="2c9c7-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="2c9c7-121">Přehled produktu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c9c7-121">Windows Forms Overview</span></span>](../../../../docs/framework/winforms/windows-forms-overview.md)  
 <span data-ttu-id="2c9c7-122">Vysvětluje základy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2c9c7-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="2c9c7-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c9c7-123">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)  
 <span data-ttu-id="2c9c7-124">Poskytuje přehled Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2c9c7-124">Provides an overview of Windows Forms.</span></span>
