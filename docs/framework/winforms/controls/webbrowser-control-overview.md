---
title: WebBrowser – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: 919098fd5eb6578b91a7b44cf99ba3aef9076081
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610978"
---
# <a name="webbrowser-control-overview"></a>WebBrowser – přehled ovládacího prvku
<xref:System.Windows.Forms.WebBrowser> Řízení poskytuje spravované obálky ovládacího prvku WebBrowser ActiveX. Spravovaná obálka umožňuje zobrazení webové stránky v klientských aplikací Windows Forms. Můžete použít <xref:System.Windows.Forms.WebBrowser> ovládacího prvku na duplicitní funkce procházení webové Internet Explorer v aplikaci nebo je můžete zakázat výchozí funkce Internet Exploreru a pomocí ovládacího prvku jako jednoduchý prohlížeče dokumentu HTML. Můžete také použít ovládací prvek do formuláře přidat prvky DHTML podle uživatelského rozhraní a skrýt skutečnost, že jsou hostované v <xref:System.Windows.Forms.WebBrowser> ovládacího prvku. Tento přístup umožňuje bez problémů kombinovat webové ovládací prvky pomocí ovládacích prvků Windows Forms v jedné aplikaci.  
  
## <a name="frequently-used-properties-methods-and-events"></a>Často používané vlastnosti, metody a události  
 <xref:System.Windows.Forms.WebBrowser> Ovládací prvek má několik vlastností, metody a události, které můžete použít k implementaci ovládacích prvků v aplikaci Internet Explorer. Například můžete použít `Navigate` metody k implementaci adresního řádku a `GoBack`, `GoForward`, `Stop`, a `Refresh` metody k implementaci navigační tlačítka na panelu nástrojů. Dokáže zpracovat `Navigated` událost k aktualizaci do adresního řádku s hodnotou `Url` vlastnost a záhlaví s hodnotou `DocumentTitle` vlastnost.  
  
 Pokud chcete generovat vlastní obsah stránky v rámci vaší aplikace, můžete nastavit `DocumentText` vlastnost. Pokud jste se seznámili s HTML modelu objektu dokumentu (DOM), můžete také manipulovat s obsahem aktuální webové stránky prostřednictvím `Document` vlastnost. Pomocí této vlastnosti můžete ukládat a úpravy dokumentů v paměti namísto procházení mezi soubory.  
  
 `Document` Vlastnost také umožňuje volat metody implementované v skriptovací kód z kódu klienta aplikace webové stránky. Chcete-li přístup ke kódu aplikace klienta z kódu skriptu, nastavte `ObjectForScripting` vlastnost. Objekt, který zadáte, je přístupný ve vašem skriptovacím kódu jako `window.external` objektu.  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> Vlastnost|Získá objekt, který poskytuje spravovaný přístup k modelu objektu dokumentu (DOM) HTML aktuální webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Události|Nastane, když se dokončí načtení webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> Vlastnost|Získá nebo nastaví obsah aktuální webové stránky HTML.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> Vlastnost|Získá název aktuální webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> – Metoda|Přejde na předchozí stránku v historii.|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> – Metoda|Přejde na další stránce v historii.|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> – Metoda|Přejde na zadanou adresu URL.|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> Události|Vyvolá se před zahájením navigace, povolíte akce, která má být zrušena.|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> Vlastnost|Získá nebo nastaví objekt, který webovou stránku skriptovací kód můžete použít ke komunikaci s vaší aplikací.|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> – Metoda|Vytiskne aktuální webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> – Metoda|Znovu načte aktuální webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> – Metoda|Zastaví aktuální navigace a zastavení dynamický stránky prvky, jako jsou zvuky a animace.|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> Vlastnost|Získá nebo nastaví adresu URL aktuální webové stránky. Nastavení této vlastnosti přejde na novou adresu URL ovládacího prvku.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>
- <xref:System.Windows.Forms.WebBrowserEncryptionLevel>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>
- <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>
- <xref:System.Windows.Forms.WebBrowserReadyState>
- <xref:System.Windows.Forms.WebBrowserRefreshOption>
- [Postupy: Přejděte na adresu URL pomocí ovládacího prvku WebBrowser](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Postupy: Tisk pomocí ovládacího prvku WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
- [Postupy: Přidání schopností webového prohlížeče do formulářové aplikaci Windows](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [Postupy: Vytvoření prohlížeče dokumentu HTML ve formulářové aplikaci Windows](../../../../docs/framework/winforms/controls/how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [Postupy: Implementace obousměrné komunikace mezi kódem DHTML a kódem klientské aplikace](../../../../docs/framework/winforms/controls/implement-two-way-com-between-dhtml-and-client.md)
- [WebBrowser – zabezpečení](../../../../docs/framework/winforms/controls/webbrowser-security.md)
