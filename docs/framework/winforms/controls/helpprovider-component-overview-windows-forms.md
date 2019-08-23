---
title: HelpProvider – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
ms.openlocfilehash: cefc590bb3011b282392504a78ac5c393c58493e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965699"
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="8ccaf-102">HelpProvider – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8ccaf-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="8ccaf-103">Komponenta model Windows Forms [HelpProvider –](helpprovider-component-windows-forms.md) se používá k přidružení souboru s nápovědě HTML 1. x (soubor. chm vytvořený pomocí HTML Help Workshop nebo souboru. htm) s vaší aplikací pro Windows.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-103">The Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="8ccaf-104">Můžete vám poskytnout celou řadu různých způsobů:</span><span class="sxs-lookup"><span data-stu-id="8ccaf-104">You can provide help in a variety of ways:</span></span>  
  
- <span data-ttu-id="8ccaf-105">Poskytněte kontextovou nápovědu pro ovládací prvky na model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
- <span data-ttu-id="8ccaf-106">Poskytněte kontextovou Nápověda pro konkrétní dialogové okno nebo konkrétní ovládací prvky v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
- <span data-ttu-id="8ccaf-107">Otevřete soubor nápovědy pro konkrétní oblasti, jako je například hlavní stránka obsahu, index nebo funkce hledání.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="8ccaf-108">Použití poskytovatele pomoci</span><span class="sxs-lookup"><span data-stu-id="8ccaf-108">Using the Help Provider</span></span>  
 <span data-ttu-id="8ccaf-109">Přidání komponenty do formuláře Windows umožňuje ostatním ovládacím prvkům ve formuláři zobrazit vlastnosti <xref:System.Windows.Forms.HelpProvider> této součásti. <xref:System.Windows.Forms.HelpProvider></span><span class="sxs-lookup"><span data-stu-id="8ccaf-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="8ccaf-110">Díky tomu můžete zadat nápovědu pro ovládací prvky ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="8ccaf-111">Pomocí vlastnosti můžete k <xref:System.Windows.Forms.HelpProvider>součásti přidružitsouborsnápovědě.<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="8ccaf-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="8ccaf-112">Zadejte typ nápovědu poskytnutý voláním <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> a zadáním hodnoty <xref:System.Windows.Forms.HelpNavigator> z výčtu pro určený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="8ccaf-113">Klíčové slovo nebo téma pro nápovědu můžete zadat voláním <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="8ccaf-114">Chcete-li volitelně přidružit konkrétní řetězec v nápovědě k jinému ovládacímu <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> prvku, použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="8ccaf-115">Řetězec, který přidružíte k ovládacímu prvku pomocí této metody, se zobrazí v automaticky otevíraném okně, když uživatel stiskne klávesu F1, zatímco ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="8ccaf-116">Pokud <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nebyla nastavena, je nutné použít <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> k poskytnutí textu v nápovědě.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="8ccaf-117">Pokud jste nastavili <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> obojí i řetězec v nápovědě, bude mít <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> aplikace založené na nástroji přednost.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ccaf-118">Při zadávání cesty k souboru s <xref:System.Windows.Forms.Help.ShowHelp%2A> <xref:System.Windows.Forms.HelpProvider> pořízením v metodě nebo <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnosti ovládacího prvku mohou nastat problémy s použitím relativní cesty.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-118">You may encounter problems using the relative path when specifying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="8ccaf-119">V takovém případě nezapomeňte použít absolutní cestu k souboru pro zadání souboru s příponou.</span><span class="sxs-lookup"><span data-stu-id="8ccaf-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ccaf-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ccaf-120">See also</span></span>

- [<span data-ttu-id="8ccaf-121">Systémy nápovědy ve formulářových aplikacích Windows</span><span class="sxs-lookup"><span data-stu-id="8ccaf-121">Help Systems in Windows Forms Applications</span></span>](../advanced/help-systems-in-windows-forms-applications.md)
