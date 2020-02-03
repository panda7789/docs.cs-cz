---
title: Integrace uživatelské nápovědě
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
ms.openlocfilehash: c402615d68c75327613d21bd35f1587b10f1dbf3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731577"
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="1d8fe-102">Integrace uživatelské nápovědy do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="1d8fe-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="1d8fe-103">Zásadní, ale často přehlédnutíný aspekt sestavování aplikací založených na systému Windows je systém nápovědy, protože je v tomto případě uživatelům zapnuta pomoc v časech nejasností.</span><span class="sxs-lookup"><span data-stu-id="1d8fe-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="1d8fe-104">Model Windows Forms podporují dva různé typy pomoci, které jsou poskytovány [komponentou HelpProvider –](../controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1d8fe-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="1d8fe-105">První z nich spočívá v tom, že uživatel odkazuje na soubor Help HTML nebo HTML Help 1. formát *x* nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="1d8fe-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="1d8fe-106">Druhý může zobrazit stručný popis "What to this" na jednotlivých ovládacích prvcích; To je užitečné hlavně pro dialogová okna.</span><span class="sxs-lookup"><span data-stu-id="1d8fe-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="1d8fe-107">Oba typy nápovědě lze použít ve stejném formuláři.</span><span class="sxs-lookup"><span data-stu-id="1d8fe-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="1d8fe-108">Kromě toho lze [komponentu ToolTip](../controls/tooltip-component-windows-forms.md) použít k poskytnutí individuální nápovědy pro ovládací prvky na model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1d8fe-108">Additionally, the [ToolTip Component](../controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d8fe-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1d8fe-109">In This Section</span></span>  
 [<span data-ttu-id="1d8fe-110">Postupy: Poskytnutí nápovědy v aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="1d8fe-110">How to: Provide Help in a Windows Application</span></span>](how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="1d8fe-111">Vysvětluje, jak používat komponentu `HelpProvider` k propojení ovládacích prvků se soubory v systému.</span><span class="sxs-lookup"><span data-stu-id="1d8fe-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="1d8fe-112">Postupy: Zobrazení místní nápovědy</span><span class="sxs-lookup"><span data-stu-id="1d8fe-112">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)  
 <span data-ttu-id="1d8fe-113">Vysvětluje, jak použít komponentu `HelpProvider` k zobrazení místní nápovědy v model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1d8fe-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="1d8fe-114">Nápověda ovládacího prvku pomocí ToolTips</span><span class="sxs-lookup"><span data-stu-id="1d8fe-114">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)  
 <span data-ttu-id="1d8fe-115">Popisuje použití komponenty `ToolTip` k zobrazení pomoci pro konkrétní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="1d8fe-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1d8fe-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1d8fe-116">Related Sections</span></span>  
 [<span data-ttu-id="1d8fe-117">Komponenta HelpProvider</span><span class="sxs-lookup"><span data-stu-id="1d8fe-117">HelpProvider Component</span></span>](../controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="1d8fe-118">Vysvětluje základy součásti `HelpProvider`.</span><span class="sxs-lookup"><span data-stu-id="1d8fe-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="1d8fe-119">Komponenta ToolTip</span><span class="sxs-lookup"><span data-stu-id="1d8fe-119">ToolTip Component</span></span>](../controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="1d8fe-120">Vysvětluje základy součásti `ToolTip`.</span><span class="sxs-lookup"><span data-stu-id="1d8fe-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="1d8fe-121">Přehled produktu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d8fe-121">Windows Forms Overview</span></span>](../windows-forms-overview.md)  
 <span data-ttu-id="1d8fe-122">Vysvětluje základy model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1d8fe-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="1d8fe-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d8fe-123">Windows Forms</span></span>](../index.md)  
 <span data-ttu-id="1d8fe-124">Poskytuje přehled model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1d8fe-124">Provides an overview of Windows Forms.</span></span>
