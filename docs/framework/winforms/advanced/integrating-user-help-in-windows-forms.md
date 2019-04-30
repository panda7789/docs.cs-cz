---
title: Integrace uživatelské nápovědy do formulářů Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
ms.openlocfilehash: 207ceeafa2ea06340310577c636deb5ea1977aae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942919"
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="9c2bc-102">Integrace uživatelské nápovědy do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="9c2bc-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="9c2bc-103">Základní, ale často přehlíženým aspekty vytváření aplikací založených na Windows je systém nápovědy, protože se jedná, kde uživatelé zapnout pro pomoc s časy záměny.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="9c2bc-104">Windows Forms – podpora dva různé typy nápovědy, každý poskytované [HelpProvider – komponenta](../controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9c2bc-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="9c2bc-105">První zahrnuje odkazující uživatele na soubor nápovědy HTML nebo 1 Nápověda jazyka HTML. *x* nebo větší formátu.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="9c2bc-106">Druhá můžete zobrazit stručný "Co je to"-typ nápovědy v jednotlivých ovládacích prvků; To je zvláště užitečná v dialogových oknech.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="9c2bc-107">Oba typy nápovědy je možné ve stejném formuláři.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="9c2bc-108">Kromě toho [ToolTip – komponenta](../controls/tooltip-component-windows-forms.md) slouží k poskytnutí nápovědy v jednotlivých ovládacích prvků ve Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-108">Additionally, the [ToolTip Component](../controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c2bc-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9c2bc-109">In This Section</span></span>  
 [<span data-ttu-id="9c2bc-110">Postupy: Poskytnutí nápovědy v aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="9c2bc-110">How to: Provide Help in a Windows Application</span></span>](how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="9c2bc-111">Vysvětluje způsob používání `HelpProvider` součásti ovládacích prvků na odkaz na soubory v systému nápovědy.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="9c2bc-112">Postupy: Zobrazení místní nápovědy</span><span class="sxs-lookup"><span data-stu-id="9c2bc-112">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)  
 <span data-ttu-id="9c2bc-113">Vysvětluje způsob používání `HelpProvider` součásti k zobrazení místní nápovědy v modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="9c2bc-114">Nápověda ovládacího prvku pomocí ToolTips</span><span class="sxs-lookup"><span data-stu-id="9c2bc-114">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)  
 <span data-ttu-id="9c2bc-115">Popisuje použití `ToolTip` komponenta zobrazit nápovědu pro konkrétní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9c2bc-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9c2bc-116">Related Sections</span></span>  
 [<span data-ttu-id="9c2bc-117">Komponenta HelpProvider</span><span class="sxs-lookup"><span data-stu-id="9c2bc-117">HelpProvider Component</span></span>](../controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="9c2bc-118">Vysvětluje základy tohoto `HelpProvider` komponenty.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="9c2bc-119">Komponenta ToolTip</span><span class="sxs-lookup"><span data-stu-id="9c2bc-119">ToolTip Component</span></span>](../controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="9c2bc-120">Vysvětluje základy tohoto `ToolTip` komponenty.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="9c2bc-121">Přehled produktu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c2bc-121">Windows Forms Overview</span></span>](../windows-forms-overview.md)  
 <span data-ttu-id="9c2bc-122">Vysvětluje základy formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="9c2bc-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c2bc-123">Windows Forms</span></span>](../index.md)  
 <span data-ttu-id="9c2bc-124">Poskytuje přehled o Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-124">Provides an overview of Windows Forms.</span></span>
