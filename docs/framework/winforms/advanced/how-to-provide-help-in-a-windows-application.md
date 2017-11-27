---
title: "Postupy: Poskytnutí nápovědy v aplikaci Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0f407f1c17c67ec99f4499b89c49932a4ba6d32c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Postupy: Poskytnutí nápovědy v aplikaci Windows
Můžete použít nástroje <xref:System.Windows.Forms.HelpProvider> součásti pro připojení ke konkrétní ovládacích prvků ve Windows Forms témata nápovědy v souboru nápovědy. Soubor nápovědy může být HTML nebo HTMLHelp 1.x nebo větší formát.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-provide-help"></a>K poskytnutí nápovědy  
  
1.  Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.HelpProvider> součásti do svého formuláře.  
  
     Součást se bude nacházet na hlavním panelu v dolní části Návrhář formulářů Windows.  
  
2.  V **vlastnosti** nastavte <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnost chm., .col nebo .htm souboru nápovědy.  
  
3.  Vyberte jiný ovládací prvek máte ve formuláři a v **vlastnosti** nastavte <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> vlastnost.  
  
     Toto je řetězec předána <xref:System.Windows.Forms.HelpProvider> součásti k souboru nápovědy k výzvě příslušné téma nápovědy.  
  
4.  V **vlastnosti** nastavte <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> vlastnost na hodnotu <xref:System.Windows.Forms.HelpNavigator> výčtu.  
  
     Určuje, jakým způsobem **HelpKeyword** předána vlastnost systému nápovědy. V následující tabulce jsou uvedeny možné nastavení a jejich popisy.  
  
    |Název členu|Popis|  
    |-----------------|-----------------|  
    |AssociateIndex|Určuje, že index pro zadaný téma se provádí v zadané adrese URL.|  
    |Najít|Určuje, že se zobrazí stránka hledat zadaná adresa URL.|  
    |Index|Určuje, že se zobrazí index zadaná adresa URL.|  
    |KeywordIndex|Určuje klíčového slova pro vyhledávání a pro případ v zadané adrese URL.|  
    |TableOfContents|Určuje, že se zobrazí obsah souboru nápovědy HTML 1.0.|  
    |Téma|Určuje, že se zobrazí v tématu odkazuje na zadanou adresu URL.|  
  
 V době běhu, stisknutím klávesy F1 při ovládacího prvku – pro které jste nastavili **HelpKeyword** a **HelpNavigator** vlastnosti – má fokus se otevře soubor nápovědy přidružené který <xref:System.Windows.Forms.HelpProvider> součásti.  
  
 V současné době **HelpNamespace** vlastnost podporuje v následujících formátech tři soubory nápovědy: HTMLHelp 1.x HTMLHelp 2.0 a HTML. Proto můžete nastavit **HelpNamespace** vlastnost na adresu http://, jako je například na webové stránce. Když toto dokončíte, otevře výchozí prohlížeč na webovou stránku s řetězec zadaný v poli **HelpKeyword** vlastnost použitá jako ukotvení. Ukotvení se používá k přejít na určitou část stránku HTML.  
  
> [!IMPORTANT]
>  Pečlivě zkontrolujte všechny informace, které se odesílá z klienta před jeho použitím ve vaší aplikaci. Uživatelé se zlými úmysly se může pokusit odeslat nebo vložit spustitelný soubor skriptu, příkazy SQL nebo jiný kód. Před zobrazení vstupu uživatele, uložte ho do databáze nebo s ním pracovat, zkontrolujte, zda neobsahuje potenciálně nebezpečného informace. Typické způsobem kontroly je použijte regulární výraz k vyhledání klíčová slova, jako je například "Skript", když obdrží vstup od uživatele.  
  
 Můžete také <xref:System.Windows.Forms.HelpProvider> součást zobrazit automaticky otevírané okno nápovědu, i když máte konfigurace. Chcete-li zobrazit soubory nápovědy pro ovládací prvky Windows Forms. Další informace najdete v tématu [postupy: zobrazení místní nápovědy](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: zobrazení místní nápovědy](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [Nápověda ovládacího prvku pomocí ToolTips](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [Integrace uživatelské nápovědy do formulářů Windows](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
