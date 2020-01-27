---
title: HelpProvider – přehled komponenty
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
ms.openlocfilehash: 74d35dfa39a605cb1e1e85cc3aeda834e1c60669
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738721"
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="4ffbd-102">HelpProvider – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4ffbd-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="4ffbd-103">Komponenta model Windows Forms [HelpProvider –](helpprovider-component-windows-forms.md) se používá k přidružení souboru s nápovědě HTML 1. x (soubor. chm vytvořený pomocí HTML Help Workshop nebo souboru. htm) s vaší aplikací pro Windows.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-103">The Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="4ffbd-104">Můžete vám poskytnout celou řadu různých způsobů:</span><span class="sxs-lookup"><span data-stu-id="4ffbd-104">You can provide help in a variety of ways:</span></span>  
  
- <span data-ttu-id="4ffbd-105">Poskytněte kontextovou nápovědu pro ovládací prvky na model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
- <span data-ttu-id="4ffbd-106">Poskytněte kontextovou Nápověda pro konkrétní dialogové okno nebo konkrétní ovládací prvky v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
- <span data-ttu-id="4ffbd-107">Otevřete soubor nápovědy pro konkrétní oblasti, jako je například hlavní stránka obsahu, index nebo funkce hledání.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="4ffbd-108">Použití poskytovatele pomoci</span><span class="sxs-lookup"><span data-stu-id="4ffbd-108">Using the Help Provider</span></span>  
 <span data-ttu-id="4ffbd-109">Přidání komponenty <xref:System.Windows.Forms.HelpProvider> do formuláře Windows umožňuje ostatním ovládacím prvkům ve formuláři vystavit vlastnosti Help komponenty <xref:System.Windows.Forms.HelpProvider>.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="4ffbd-110">Díky tomu můžete zadat nápovědu pro ovládací prvky ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="4ffbd-111">Pomocí vlastnosti <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> můžete k součásti <xref:System.Windows.Forms.HelpProvider> přidružit soubor s příponou.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="4ffbd-112">Zadejte typ nápovědu, která se poskytuje, voláním <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> a zadáním hodnoty z výčtu <xref:System.Windows.Forms.HelpNavigator> daného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="4ffbd-113">Klíčové slovo nebo téma pro nápovědu můžete zadat voláním metody <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="4ffbd-114">Volitelně můžete k přidružení konkrétního řetězce v nápovědě k jinému ovládacímu prvku použít metodu <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="4ffbd-115">Řetězec, který přidružíte k ovládacímu prvku pomocí této metody, se zobrazí v automaticky otevíraném okně, když uživatel stiskne klávesu F1, zatímco ovládací prvek má fokus.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="4ffbd-116">Pokud <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nebyla nastavena, je nutné zadat text v nápovědě pomocí <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="4ffbd-117">Pokud jste nastavili <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> i řetězec v nápovědě, bude mít aplikace na základě <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> přednost.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ffbd-118">Při zadávání cesty k souboru Help v metodě <xref:System.Windows.Forms.Help.ShowHelp%2A> nebo vlastnosti <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> ovládacího prvku <xref:System.Windows.Forms.HelpProvider> můžete narazit na problémy s použitím relativní cesty.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-118">You may encounter problems using the relative path when specifying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="4ffbd-119">V takovém případě nezapomeňte použít absolutní cestu k souboru pro zadání souboru s příponou.</span><span class="sxs-lookup"><span data-stu-id="4ffbd-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ffbd-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ffbd-120">See also</span></span>

- [<span data-ttu-id="4ffbd-121">Systémy nápovědy ve formulářových aplikacích Windows</span><span class="sxs-lookup"><span data-stu-id="4ffbd-121">Help Systems in Windows Forms Applications</span></span>](../advanced/help-systems-in-windows-forms-applications.md)
