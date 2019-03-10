---
title: 'Postupy: Poskytnutí nápovědy v aplikaci Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
ms.openlocfilehash: bb05842eb7cd30611c68f685ea3dae9200d87d35
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724931"
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Postupy: Poskytnutí nápovědy v aplikaci Windows
Lze použít <xref:System.Windows.Forms.HelpProvider> součásti pro připojení témata nápovědy v souboru nápovědy k určité ovládací prvky v modelu Windows Forms. Soubor nápovědy může být ve formátu HTML nebo HTMLHelp 1.x nebo větší formátu.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-provide-help"></a>Získání nápovědy  
  
1.  Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.HelpProvider> komponentu do formuláře.  
  
     Komponenta se bude nacházet na hlavním panelu v dolní části Návrháře formulářů Windows.  
  
2.  V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnost v souboru nápovědy chm, .col nebo htm.  
  
3.  Vyberte jiný ovládací prvek na formuláři máte a v **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> vlastnost.  
  
     Jedná se o řetězec, který předává <xref:System.Windows.Forms.HelpProvider> komponentu do souboru nápovědy k výzvě příslušné téma nápovědy.  
  
4.  V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> vlastnost na hodnotu <xref:System.Windows.Forms.HelpNavigator> výčtu.  
  
     Určuje, jakým způsobem **HelpKeyword** vlastnost předána do systému nápovědy. V následující tabulce jsou uvedeny možné nastavení a jejich popisy.  
  
    |Název členu|Popis|  
    |-----------------|-----------------|  
    |AssociateIndex|Určuje, že index určené téma se provádí v zadané adrese URL.|  
    |Vyhledávání|Určuje, že se zobrazí stránka hledat zadaná adresa URL.|  
    |Index|Určuje, že se zobrazí index zadané adresy URL.|  
    |KeywordIndex|Určuje klíčové slovo k vyhledání a akce má být provedena v zadané adrese URL.|  
    |TableOfContents|Určuje, že se zobrazí obsah souboru nápovědy HTML 1.0.|  
    |Téma|Určuje, že se zobrazí téma odkazuje na zadanou adresu URL.|  
  
 V době běhu, stisknutím klávesy F1 při ovládacího prvku – pro které jste nastavili **HelpKeyword** a **HelpNavigator** vlastnosti – má fokus, otevře se soubor nápovědy spojený s ním <xref:System.Windows.Forms.HelpProvider> komponenty.  
  
 V současné době **HelpNamespace** vlastnost podporuje soubory nápovědy ve třech následujících formátech: HTMLHelp 1.x HTMLHelp 2.0 a ve formátu HTML. Proto můžete nastavit **HelpNamespace** nastavte na adresu http://, jako je například na webové stránce. Pokud to uděláte, otevře se výchozí prohlížeč na webovou stránku s řetězec zadaný v poli **HelpKeyword** vlastnost použit jako ukotvení. Ukotvení se používá pro přechod na určitou část stránku HTML.  
  
> [!IMPORTANT]
>  Pečlivě zkontrolujte všechny informace odesílané z klienta před jeho použitím v aplikaci. Uživatelé se zlými úmysly se může pokusit o odeslání nebo vložit spustitelný soubor skriptu, příkazy SQL nebo jiný kód. Před zobrazení vstupu uživatele, ukládat v databázi nebo s ním pracovat, zkontrolujte neobsahuje informace o potenciálně nebezpečné. Typické způsob, jak zkontrolovat je použit regulární výraz k vyhledání klíčová slova, jako je "Skript" při přijímání vstupu od uživatele.  
  
 Můžete také použít <xref:System.Windows.Forms.HelpProvider> součásti k zobrazení místní nápovědy, i v případě, že jste si ji nakonfigurovali zobrazíte soubory nápovědy pro ovládací prvky ve formulářích Windows. Další informace najdete v tématu [jak: Zobrazení místní nápovědy](how-to-display-pop-up-help.md).  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Zobrazení místní nápovědy](how-to-display-pop-up-help.md)
- [Nápověda ovládacího prvku pomocí ToolTips](control-help-using-tooltips.md)
- [Integrace uživatelské nápovědy v modelu Windows Forms](integrating-user-help-in-windows-forms.md)
- [Windows Forms](../index.md)
