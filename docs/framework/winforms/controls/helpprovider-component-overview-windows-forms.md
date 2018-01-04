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
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider – přehled komponenty (Windows Forms)
Windows Forms [HelpProvider –](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) součást je použito k přidružení soubor nápovědy HTML – Nápověda 1.x (soubor CHM. vytvořeného s pracoviště Nápověda HTML nebo soubor HTM) s aplikací pro Windows. Můžete poskytnutí nápovědy v mnoha různými způsoby:  
  
-   Zadejte Kontextová nápověda pro ovládací prvky na formuláři Windows.  
  
-   Zadejte Kontextová nápověda na konkrétní dialogové okno nebo konkrétní ovládací prvky v dialogovém okně.  
  
-   Otevřete soubor nápovědy pro konkrétní oblasti, například na hlavní stránku obsahu, Index nebo funkce vyhledávání.  
  
## <a name="using-the-help-provider"></a>Pomocí zprostředkovatele nápovědy  
 Přidání <xref:System.Windows.Forms.HelpProvider> součást do svého formuláře systému Windows umožňuje další ovládací prvky na formuláři vystavit vlastnosti nápovědy <xref:System.Windows.Forms.HelpProvider> součásti. To umožňuje poskytovat nápovědu pro ovládací prvky na formuláři Windows. Soubor nápovědy se můžete přidružit <xref:System.Windows.Forms.HelpProvider> pomocí součásti <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnost. Zadejte typ nápovědy poskytované volání <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> a poskytování hodnotu z <xref:System.Windows.Forms.HelpNavigator> výčtu pro daný ovládací prvek. Zadejte – klíčové slovo nebo téma o pomoc při volání <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> metoda.  
  
 Volitelně můžete přidružit další ovládací prvek konkrétní řetězec nápovědy, pomocí <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> metoda. Řetězec, který přidružíte s ovládacím prvkem pomocí této metody se zobrazí v místním okně po stisknutí klávesy F1 při řízení má právě fokus.  
  
 Pokud <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nebyl nastaven, je nutné použít <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> zajistit text nápovědy. Pokud jste nastavili i <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> a řetězec nápovědy, na základě nápovědy <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> bude mít přednost.  
  
> [!NOTE]
>  Můžete setkat s problémy pomocí relativní cesty při zadání cestu k souboru nápovědy v <xref:System.Windows.Forms.Help.ShowHelp%2A> metoda nebo <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnost <xref:System.Windows.Forms.HelpProvider> ovládacího prvku. Jako takový je nutné použít absolutní cestu k souboru k určení v souboru nápovědy.  
  
## <a name="see-also"></a>Viz také  
 [Systémy nápovědy ve formulářových aplikacích Windows](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)
