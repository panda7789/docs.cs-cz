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
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider – přehled komponenty (Windows Forms)
Komponenta model Windows Forms [HelpProvider –](helpprovider-component-windows-forms.md) se používá k přidružení souboru s nápovědě HTML 1. x (soubor. chm vytvořený pomocí HTML Help Workshop nebo souboru. htm) s vaší aplikací pro Windows. Můžete vám poskytnout celou řadu různých způsobů:  
  
- Poskytněte kontextovou nápovědu pro ovládací prvky na model Windows Forms.  
  
- Poskytněte kontextovou Nápověda pro konkrétní dialogové okno nebo konkrétní ovládací prvky v dialogovém okně.  
  
- Otevřete soubor nápovědy pro konkrétní oblasti, jako je například hlavní stránka obsahu, index nebo funkce hledání.  
  
## <a name="using-the-help-provider"></a>Použití poskytovatele pomoci  
 Přidání komponenty do formuláře Windows umožňuje ostatním ovládacím prvkům ve formuláři zobrazit vlastnosti <xref:System.Windows.Forms.HelpProvider> této součásti. <xref:System.Windows.Forms.HelpProvider> Díky tomu můžete zadat nápovědu pro ovládací prvky ve formuláři Windows. Pomocí vlastnosti můžete k <xref:System.Windows.Forms.HelpProvider>součásti přidružitsouborsnápovědě.<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> Zadejte typ nápovědu poskytnutý voláním <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> a zadáním hodnoty <xref:System.Windows.Forms.HelpNavigator> z výčtu pro určený ovládací prvek. Klíčové slovo nebo téma pro nápovědu můžete zadat voláním <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> metody.  
  
 Chcete-li volitelně přidružit konkrétní řetězec v nápovědě k jinému ovládacímu <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> prvku, použijte metodu. Řetězec, který přidružíte k ovládacímu prvku pomocí této metody, se zobrazí v automaticky otevíraném okně, když uživatel stiskne klávesu F1, zatímco ovládací prvek má fokus.  
  
 Pokud <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nebyla nastavena, je nutné použít <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> k poskytnutí textu v nápovědě. Pokud jste nastavili <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> obojí i řetězec v nápovědě, bude mít <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> aplikace založené na nástroji přednost.  
  
> [!NOTE]
> Při zadávání cesty k souboru s <xref:System.Windows.Forms.Help.ShowHelp%2A> <xref:System.Windows.Forms.HelpProvider> pořízením v metodě nebo <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnosti ovládacího prvku mohou nastat problémy s použitím relativní cesty. V takovém případě nezapomeňte použít absolutní cestu k souboru pro zadání souboru s příponou.  
  
## <a name="see-also"></a>Viz také:

- [Systémy nápovědy ve formulářových aplikacích Windows](../advanced/help-systems-in-windows-forms-applications.md)
