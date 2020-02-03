---
title: Přehled komponenty HelpProvider
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
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider – přehled komponenty (Windows Forms)
Komponenta model Windows Forms [HelpProvider –](helpprovider-component-windows-forms.md) se používá k přidružení souboru s nápovědě HTML 1. x (soubor. chm vytvořený pomocí HTML Help Workshop nebo souboru. htm) s vaší aplikací pro Windows. Můžete vám poskytnout celou řadu různých způsobů:  
  
- Poskytněte kontextovou nápovědu pro ovládací prvky na model Windows Forms.  
  
- Poskytněte kontextovou Nápověda pro konkrétní dialogové okno nebo konkrétní ovládací prvky v dialogovém okně.  
  
- Otevřete soubor nápovědy pro konkrétní oblasti, jako je například hlavní stránka obsahu, index nebo funkce hledání.  
  
## <a name="using-the-help-provider"></a>Použití poskytovatele pomoci  
 Přidání komponenty <xref:System.Windows.Forms.HelpProvider> do formuláře Windows umožňuje ostatním ovládacím prvkům ve formuláři vystavit vlastnosti Help komponenty <xref:System.Windows.Forms.HelpProvider>. Díky tomu můžete zadat nápovědu pro ovládací prvky ve formuláři Windows. Pomocí vlastnosti <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> můžete k součásti <xref:System.Windows.Forms.HelpProvider> přidružit soubor s příponou. Zadejte typ nápovědu, která se poskytuje, voláním <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> a zadáním hodnoty z výčtu <xref:System.Windows.Forms.HelpNavigator> daného ovládacího prvku. Klíčové slovo nebo téma pro nápovědu můžete zadat voláním metody <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>.  
  
 Volitelně můžete k přidružení konkrétního řetězce v nápovědě k jinému ovládacímu prvku použít metodu <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>. Řetězec, který přidružíte k ovládacímu prvku pomocí této metody, se zobrazí v automaticky otevíraném okně, když uživatel stiskne klávesu F1, zatímco ovládací prvek má fokus.  
  
 Pokud <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nebyla nastavena, je nutné zadat text v nápovědě pomocí <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>. Pokud jste nastavili <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> i řetězec v nápovědě, bude mít aplikace na základě <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> přednost.  
  
> [!NOTE]
> Při zadávání cesty k souboru Help v metodě <xref:System.Windows.Forms.Help.ShowHelp%2A> nebo vlastnosti <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> ovládacího prvku <xref:System.Windows.Forms.HelpProvider> můžete narazit na problémy s použitím relativní cesty. V takovém případě nezapomeňte použít absolutní cestu k souboru pro zadání souboru s příponou.  
  
## <a name="see-also"></a>Viz také

- [Systémy nápovědy ve formulářových aplikacích Windows](../advanced/help-systems-in-windows-forms-applications.md)
