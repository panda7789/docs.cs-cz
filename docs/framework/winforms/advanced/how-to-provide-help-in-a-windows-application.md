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
ms.openlocfilehash: 405de333ce936a864047e827e60f56a930059e26
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143602"
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Postupy: Poskytnutí nápovědy v aplikaci Windows

Pomocí komponenty můžete v <xref:System.Windows.Forms.HelpProvider> souboru nápovědy připojit témata nápovědy ke konkrétním ovládacím prvkům na model Windows Forms. Soubor Help může být HTML nebo HTMLHelp 1. x nebo vyšší.

## <a name="provide-help"></a>Poskytnout pomocníka

1. V sadě Visual Studio, z **panelu nástrojů**přetáhněte <xref:System.Windows.Forms.HelpProvider> komponentu do formuláře.

     Komponenta se bude nacházet v zásobníku v dolní části Návrhář formulářů.

2. V okně **vlastnosti** nastavte <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> vlastnost na soubor Help. chm,. slo nebo. htm.

3. Vyberte jiný ovládací prvek, který máte ve formuláři, a v okně **vlastnosti** nastavte <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> vlastnost.

     Toto je řetězec předaný <xref:System.Windows.Forms.HelpProvider> komponentě souboru nápovědy k předvolání příslušného tématu nápovědy.

4. V okně **vlastnosti** nastavte <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> vlastnost na hodnotu <xref:System.Windows.Forms.HelpNavigator> výčtu.

     To určuje způsob, jakým je vlastnost **HelpKeyword** předána systému help. V následující tabulce jsou uvedena možná nastavení a jejich popisy.

    |Název členu|Popis|
    |-----------------|-----------------|
    |AssociateIndex|Určuje, že se index zadaného tématu provede v zadané adrese URL.|
    |Vyhledávání|Určuje, že se zobrazí stránka vyhledávání v zadané adrese URL.|
    |Index|Určuje, že se zobrazí index zadané adresy URL.|
    |KeywordIndex|Určuje klíčové slovo, které chcete vyhledat, a akci, která se má provést v zadané adrese URL.|
    |TableOfContents|Určuje, že se zobrazí tabulka obsahu souboru nápovědy HTML 1,0.|
    |Téma|Určuje, že se zobrazí téma odkazované zadanou adresou URL.|

 V době běhu stiskněte klávesu F1, když ovládací prvek, pro který jste nastavili vlastnosti **HelpKeyword** a **HelpNavigator** – má fokus, otevře se soubor s nápovědu, který se k této <xref:System.Windows.Forms.HelpProvider> komponentě přidruží.

 V současné době vlastnost **HelpNamespace** podporuje soubory Help v následujících třech formátech: HTMLHelp 1. x, HTMLHelp 2,0 a HTML. Proto můžete vlastnost **HelpNamespace** nastavit na `http://` adresu, jako je například webová stránka. Pokud k tomu dojde, otevře se výchozí prohlížeč na webové stránce s řetězcem zadaným ve vlastnosti **HelpKeyword** použité jako kotvy. Kotva se používá k přechodu na určitou část stránky HTML.

> [!IMPORTANT]
> Nezapomeňte si ověřit, jestli jsou informace odesílané z klienta před jeho použitím ve vaší aplikaci opatrní. Uživatelé se zlými úmysly se můžou pokusit odeslat nebo vložit spustitelný skript, příkazy SQL nebo jiný kód. Než zobrazíte vstup uživatele, uložte ho do databáze nebo s ním můžete pracovat, ověřte, že neobsahuje potenciálně nebezpečné informace. Obvyklým způsobem, jak zkontrolovat, je použít regulární výraz pro hledání klíčových slov, jako je například "SCRIPT", když obdržíte vstup od uživatele.

Můžete také použít <xref:System.Windows.Forms.HelpProvider> komponentu k zobrazení místní nápovědy, i když je máte nakonfigurovanou tak, aby zobrazovala soubory nápovědy pro ovládací prvky na model Windows Forms. Další informace najdete v tématu [Postup: zobrazení místní nápovědy](how-to-display-pop-up-help.md).

## <a name="see-also"></a>Viz také

- [Postupy: Zobrazení místní nápovědy](how-to-display-pop-up-help.md)
- [Nápověda ovládacího prvku pomocí ToolTips](control-help-using-tooltips.md)
- [Integrace uživatelské nápovědy v modelu Windows Forms](integrating-user-help-in-windows-forms.md)
- [Windows Forms](../index.md)
