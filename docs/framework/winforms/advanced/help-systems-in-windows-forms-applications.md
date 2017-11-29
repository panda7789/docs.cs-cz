---
title: "Systémy nápovědy ve formulářových aplikacích Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45d3385d008f823050f213252fdc2e1851cf422b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="help-systems-in-windows-forms-applications"></a><span data-ttu-id="bd06f-102">Systémy nápovědy ve formulářových aplikacích Windows</span><span class="sxs-lookup"><span data-stu-id="bd06f-102">Help Systems in Windows Forms Applications</span></span>
<span data-ttu-id="bd06f-103">Jeden z nejdůležitějších courtesies, jako vývojář aplikací, můžete poskytnout uživatelům bez je příslušný systém nápovědy.</span><span class="sxs-lookup"><span data-stu-id="bd06f-103">One of the most important courtesies you, as a developer of applications, can furnish your users with is a competent Help system.</span></span> <span data-ttu-id="bd06f-104">Toto je, kde bude zapnout když stát nerozumíte nebo disoriented.</span><span class="sxs-lookup"><span data-stu-id="bd06f-104">This is where they will turn when they become confused or disoriented.</span></span> <span data-ttu-id="bd06f-105">Poskytnutí systému nápovědy v aplikaci systému Windows se snadno provádí pomocí [HelpProvider – komponenta](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="bd06f-105">Providing a Help system in a Windows-based application is easily done by using the [HelpProvider Component](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span></span>  
  
## <a name="different-types-of-help"></a><span data-ttu-id="bd06f-106">Různé typy nápovědy</span><span class="sxs-lookup"><span data-stu-id="bd06f-106">Different Types of Help</span></span>  
 <span data-ttu-id="bd06f-107">Windows Forms <xref:System.Windows.Forms.HelpProvider> součást je použit k přidružení soubor nápovědy HTML – Nápověda 1.x (soubor CHM. vytvořeného s pracoviště Nápověda HTML nebo soubor HTM) s vaší aplikací systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bd06f-107">The Windows Forms <xref:System.Windows.Forms.HelpProvider> component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows-based application.</span></span> <span data-ttu-id="bd06f-108"><xref:System.Windows.Forms.HelpProvider> Součást lze použít pro zajištění Kontextová nápověda ve Windows Forms – ovládací prvky nebo konkrétní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="bd06f-108">The <xref:System.Windows.Forms.HelpProvider> component can be used to provide context-sensitive Help for controls on Windows Forms or specific controls.</span></span> <span data-ttu-id="bd06f-109">Kromě toho <xref:System.Windows.Forms.HelpProvider> součást můžete otevřít soubor nápovědy pro konkrétní oblasti, například na hlavní stránku tabulky obsahu, indexu nebo funkce vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="bd06f-109">Additionally, the <xref:System.Windows.Forms.HelpProvider> component can open a Help file to specific areas, such as the main page of a table of contents, an index, or a search function.</span></span> <span data-ttu-id="bd06f-110">Obecné informace o <xref:System.Windows.Forms.HelpProvider> součást, najdete v části [HelpProvider – přehled komponenty](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="bd06f-110">For general information about the <xref:System.Windows.Forms.HelpProvider> component, see [HelpProvider Component Overview](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md).</span></span> <span data-ttu-id="bd06f-111">Informace o tom, jak používat <xref:System.Windows.Forms.HelpProvider> součásti pro zobrazení místní nápovědy v aplikaci Windows Forms, najdete v části [postupy: zobrazení místní nápovědy](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="bd06f-111">For information on how to use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help on Windows Forms, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span> <span data-ttu-id="bd06f-112">Informace o používání <xref:System.Windows.Forms.ToolTip> součást zobrazit nápovědu specifické pro ovládací prvek, najdete v části [ToolTips pomoci pomocí ovládacího prvku](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md).</span><span class="sxs-lookup"><span data-stu-id="bd06f-112">For information on using the <xref:System.Windows.Forms.ToolTip> component to show control-specific Help, see [Control Help Using ToolTips](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md).</span></span>  
  
 <span data-ttu-id="bd06f-113">Soubory nápovědy HTML 1.x s pracoviště Nápověda HTML můžete vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="bd06f-113">You can generate HTML Help 1.x files with the HTML Help Workshop.</span></span> <span data-ttu-id="bd06f-114">Další informace o HTML – Nápověda najdete v části "HTML pomůže pracoviště" nebo na další témata "HTML – Nápověda" na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="bd06f-114">For more information on HTML Help, see the "HTML Help Workshop" or the other "HTML Help" topics in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd06f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd06f-115">See Also</span></span>  
 [<span data-ttu-id="bd06f-116">Integrace uživatelské nápovědy do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="bd06f-116">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="bd06f-117">HelpProvider – komponenta</span><span class="sxs-lookup"><span data-stu-id="bd06f-117">HelpProvider Component</span></span>](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 [<span data-ttu-id="bd06f-118">ToolTip – komponenta</span><span class="sxs-lookup"><span data-stu-id="bd06f-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 [<span data-ttu-id="bd06f-119">Přehled produktu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bd06f-119">Windows Forms Overview</span></span>](../../../../docs/framework/winforms/windows-forms-overview.md)  
 [<span data-ttu-id="bd06f-120">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bd06f-120">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
