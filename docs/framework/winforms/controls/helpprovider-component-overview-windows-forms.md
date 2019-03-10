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
ms.openlocfilehash: f9cf0c165c6c64186eff53676c8b1b06f74361fc
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708376"
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider – přehled komponenty (Windows Forms)
Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) komponenta se používá pro soubor nápovědy HTML Help 1.x (soubor CHM vytvořenými pomocí HTML Help Workshop, nebo soubor HTM) přidružit k aplikaci Windows. Můžete poskytnout pomoc v mnoha různými způsoby:  
  
-   Poskytují kontextové nápovědy pro ovládacích prvků ve Windows Forms.  
  
-   Poskytují kontextové nápovědy na konkrétní dialogové okno nebo konkrétní ovládacích prvků v dialogovém okně.  
  
-   Otevřete soubor nápovědy pro konkrétní oblasti, jako je hlavní stránky obsahu, Index nebo vyhledávací funkci.  
  
## <a name="using-the-help-provider"></a>Pomocí zprostředkovatele nápovědy  
 Přidávání <xref:System.Windows.Forms.HelpProvider> komponentu do formuláře Windows umožňuje další ovládací prvky ve formuláři vystavit vlastnosti nápovědy <xref:System.Windows.Forms.HelpProvider> komponenty. To umožňuje poskytnout nápovědu pro ovládací prvky na formuláři Windows. Můžete přidružit soubor nápovědy s <xref:System.Windows.Forms.HelpProvider> pomocí komponenty <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnost. Zadejte typ nápovědy k dispozici voláním <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> a získává hodnotu z <xref:System.Windows.Forms.HelpNavigator> výčtu pro zadaný ovládací prvek. Zadejte klíčové slovo nebo téma pomoc voláním <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> metody.  
  
 Volitelně můžete přidružit konkrétní řetězec nápovědy k jiným ovládacím prvkem, použijte <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> metody. Řetězec, který přidružíte k ovládacímu prvku pomocí této metody se zobrazí v překryvném okně, když uživatel stiskne klávesu F1, kdy má ovládací prvek fokus.  
  
 Pokud <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nebyl nastaven, je nutné použít <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> k zobrazení textu nápovědy. Pokud jste nastavili i <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> a text nápovědy, na základě nápovědy <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> bude mít přednost.  
  
> [!NOTE]
>  Můžete setkat s problémy při určení cesty k souboru nápovědy v pomocí relativní cesty <xref:System.Windows.Forms.Help.ShowHelp%2A> metoda nebo <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnost <xref:System.Windows.Forms.HelpProvider> ovládacího prvku. V důsledku toho je potřeba použít absolutní cesty k určení souboru nápovědy.  
  
## <a name="see-also"></a>Viz také:
- [Systémy nápovědy ve formulářových aplikacích Windows](../advanced/help-systems-in-windows-forms-applications.md)
