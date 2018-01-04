---
title: "HelpProvider – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23a9db5f7c5286eaab50f2499845f7294af878ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="11d4a-102">HelpProvider – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="11d4a-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="11d4a-103">Windows Forms [HelpProvider –](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) součást je použito k přidružení soubor nápovědy HTML – Nápověda 1.x (soubor CHM. vytvořeného s pracoviště Nápověda HTML nebo soubor HTM) s aplikací pro Windows.</span><span class="sxs-lookup"><span data-stu-id="11d4a-103">The Windows Forms [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="11d4a-104">Můžete poskytnutí nápovědy v mnoha různými způsoby:</span><span class="sxs-lookup"><span data-stu-id="11d4a-104">You can provide help in a variety of ways:</span></span>  
  
-   <span data-ttu-id="11d4a-105">Zadejte Kontextová nápověda pro ovládací prvky na formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="11d4a-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
-   <span data-ttu-id="11d4a-106">Zadejte Kontextová nápověda na konkrétní dialogové okno nebo konkrétní ovládací prvky v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="11d4a-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
-   <span data-ttu-id="11d4a-107">Otevřete soubor nápovědy pro konkrétní oblasti, například na hlavní stránku obsahu, Index nebo funkce vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="11d4a-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="11d4a-108">Pomocí zprostředkovatele nápovědy</span><span class="sxs-lookup"><span data-stu-id="11d4a-108">Using the Help Provider</span></span>  
 <span data-ttu-id="11d4a-109">Přidání <xref:System.Windows.Forms.HelpProvider> součást do svého formuláře systému Windows umožňuje další ovládací prvky na formuláři vystavit vlastnosti nápovědy <xref:System.Windows.Forms.HelpProvider> součásti.</span><span class="sxs-lookup"><span data-stu-id="11d4a-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="11d4a-110">To umožňuje poskytovat nápovědu pro ovládací prvky na formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="11d4a-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="11d4a-111">Soubor nápovědy se můžete přidružit <xref:System.Windows.Forms.HelpProvider> pomocí součásti <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="11d4a-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="11d4a-112">Zadejte typ nápovědy poskytované volání <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> a poskytování hodnotu z <xref:System.Windows.Forms.HelpNavigator> výčtu pro daný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="11d4a-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="11d4a-113">Zadejte – klíčové slovo nebo téma o pomoc při volání <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="11d4a-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="11d4a-114">Volitelně můžete přidružit další ovládací prvek konkrétní řetězec nápovědy, pomocí <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="11d4a-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="11d4a-115">Řetězec, který přidružíte s ovládacím prvkem pomocí této metody se zobrazí v místním okně po stisknutí klávesy F1 při řízení má právě fokus.</span><span class="sxs-lookup"><span data-stu-id="11d4a-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="11d4a-116">Pokud <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nebyl nastaven, je nutné použít <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> zajistit text nápovědy.</span><span class="sxs-lookup"><span data-stu-id="11d4a-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="11d4a-117">Pokud jste nastavili i <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> a řetězec nápovědy, na základě nápovědy <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> bude mít přednost.</span><span class="sxs-lookup"><span data-stu-id="11d4a-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11d4a-118">Můžete setkat s problémy pomocí relativní cesty při zadání cestu k souboru nápovědy v <xref:System.Windows.Forms.Help.ShowHelp%2A> metoda nebo <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnost <xref:System.Windows.Forms.HelpProvider> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="11d4a-118">You may encounter problems using the relative path when specifiying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="11d4a-119">Jako takový je nutné použít absolutní cestu k souboru k určení v souboru nápovědy.</span><span class="sxs-lookup"><span data-stu-id="11d4a-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d4a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="11d4a-120">See Also</span></span>  
 [<span data-ttu-id="11d4a-121">Systémy nápovědy ve formulářových aplikacích Windows</span><span class="sxs-lookup"><span data-stu-id="11d4a-121">Help Systems in Windows Forms Applications</span></span>](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)
