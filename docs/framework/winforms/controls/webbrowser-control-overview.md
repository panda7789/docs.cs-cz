---
title: "WebBrowser – přehled ovládacího prvku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2c1ed93769cc91d9622a86ea2d894cea57f5bcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="webbrowser-control-overview"></a>WebBrowser – přehled ovládacího prvku
<xref:System.Windows.Forms.WebBrowser> Řízení poskytuje spravovaná obálka pro ovládací prvek WebBrowser ActiveX. Spravovaná obálka umožňuje zobrazení webové stránky v aplikacích Windows Forms klienta. Můžete použít <xref:System.Windows.Forms.WebBrowser> řízení duplicitní funkce procházení WWW aplikace Internet Explorer v aplikaci, nebo můžete zakázat výchozí funkce Internet Exploreru a použít ovládací prvek jako jednoduchý prohlížeče dokumentu HTML. Můžete také použít ovládací prvek přidejte do svého formuláře prvky jazyka DHTML na základě uživatelského rozhraní a skrýt skutečnost, že jsou hostované v <xref:System.Windows.Forms.WebBrowser> ovládacího prvku. Tento přístup umožňuje bezproblémově kombinovat ovládací prvky webového s ovládacími prvky Windows Forms v jedné aplikaci.  
  
## <a name="frequently-used-properties-methods-and-events"></a>Často používané vlastnosti, metod a události  
 <xref:System.Windows.Forms.WebBrowser> Ovládací prvek má několik vlastností, metod a události, které můžete použít k implementaci ovládacích prvků v Internet Exploreru. Například můžete použít `Navigate` metody k implementaci adresa a `GoBack`, `GoForward`, `Stop`, a `Refresh` metody k implementaci navigačních tlačítek na panelu nástrojů. Může zpracovat `Navigated` událostí k aktualizaci panelu Adresa s hodnotou `Url` vlastnost a záhlaví s hodnotou `DocumentTitle` vlastnost.  
  
 Pokud chcete generovat vlastní obsah stránky v rámci vaší aplikace, můžete nastavit `DocumentText` vlastnost. Pokud jste obeznámeni s modelem objektu dokumentu HTML (DOM), můžete také upravit obsah aktuální webové stránky prostřednictvím `Document` vlastnost. Pomocí této vlastnosti můžete ukládat a upravovat dokumenty v paměti místo procházení mezi soubory.  
  
 `Document` Vlastnost také umožňuje volat metody implementované webové stránce skriptovací kód z vašeho kódu aplikace klienta. Chcete-li získat přístup k kódu aplikace klienta z kódu skriptu, nastavte `ObjectForScripting` vlastnost. Objekt, který zadáte přístupná pomocí váš kód skriptu, jako `window.external` objektu.  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A>Vlastnost|Získá objekt, který poskytuje spravovaný přístup k modelu objektu dokumentu (DOM) HTML aktuální webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>události|Nastane při dokončení načítání webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A>Vlastnost|Získá nebo nastaví obsah aktuální webové stránky HTML.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A>Vlastnost|Získá název aktuální webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A>– Metoda|Přejde na předchozí stránku v historii.|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A>– Metoda|Přejde na další stránku v historii.|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A>– Metoda|Přejde na zadané adrese URL.|  
|<xref:System.Windows.Forms.WebBrowser.Navigating>události|Se vyskytuje před začátkem navigace, povolení akce, která má být zrušena.|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A>Vlastnost|Získá nebo nastaví objekt, který webovou stránku skriptovací kód můžete použít ke komunikaci s vaší aplikací.|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A>– Metoda|Vytiskne aktuální webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A>– Metoda|Znovu načte aktuální webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A>– Metoda|Zastaví aktuální navigaci a zastavuje dynamické stránky prvky, jako jsou například zvuky a animace.|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A>Vlastnost|Získá nebo nastaví adresu URL aktuální webové stránky. Nastavení této vlastnosti přejde ovládacího prvku na novou adresu URL.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserEncryptionLevel>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>  
 <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserReadyState>  
 <xref:System.Windows.Forms.WebBrowserRefreshOption>  
 [Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [Postupy: Tisk pomocí ovládacího prvku WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)  
 [Postupy: Přidání schopností webového prohlížeče do aplikace Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)  
 [Postupy: Vytvoření prohlížeče dokumentu HTML v aplikaci Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)  
 [Postupy: Implementace obousměrné komunikace mezi kódem DHTML a kódem klientské aplikace](../../../../docs/framework/winforms/controls/implement-two-way-com-between-dhtml-and-client.md)  
 [WebBrowser – zabezpečení](../../../../docs/framework/winforms/controls/webbrowser-security.md)
