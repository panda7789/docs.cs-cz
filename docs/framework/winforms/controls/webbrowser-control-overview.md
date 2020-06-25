---
title: WebBrowser – přehled ovládacího prvku
description: Naučte se používat ovládací prvek WebBrowser k bezproblémovému kombinování webových ovládacích prvků s ovládacími prvky model Windows Forms v jediné aplikaci.
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: 6a0548bb0f5905d8f848ab13fb82d32b50caa891
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325734"
---
# <a name="webbrowser-control-overview"></a>WebBrowser – přehled ovládacího prvku
<xref:System.Windows.Forms.WebBrowser>Ovládací prvek poskytuje spravovanou obálku pro ovládací prvek WebBrowser ActiveX. Spravovaná obálka umožňuje zobrazit webové stránky v klientských aplikacích model Windows Forms. Pomocí tohoto <xref:System.Windows.Forms.WebBrowser> ovládacího prvku můžete v aplikaci duplikovat funkce procházení webu aplikace Internet Explorer nebo můžete zakázat výchozí funkce aplikace Internet Explorer a používat ovládací prvek jako jednoduchý prohlížeč dokumentů HTML. Ovládací prvek lze také použít k přidání prvků uživatelského rozhraní založeného na jazyce DHTML do formuláře a skrytí faktů, které jsou hostovány v <xref:System.Windows.Forms.WebBrowser> ovládacím prvku. Tento přístup vám umožní bez problémů kombinovat webové ovládací prvky s ovládacími prvky model Windows Forms v jediné aplikaci.  
  
## <a name="frequently-used-properties-methods-and-events"></a>Často používané vlastnosti, metody a události  
 <xref:System.Windows.Forms.WebBrowser>Ovládací prvek má několik vlastností, metod a událostí, které lze použít k implementaci ovládacích prvků nalezených v aplikaci Internet Explorer. Například můžete použít `Navigate` metodu pro implementaci panelu Adresa a `GoBack` `GoForward` metody,, `Stop` a `Refresh` pro implementaci navigačních tlačítek na panelu nástrojů. Událost můžete zpracovat `Navigated` tak, aby aktualizovala adresní řádek s hodnotou `Url` vlastnosti a záhlavím s hodnotou `DocumentTitle` Vlastnosti.  
  
 Pokud chcete ve své aplikaci vygenerovat vlastní obsah stránky, můžete nastavit `DocumentText` vlastnost. Pokud jste obeznámeni s modelem DOM (Document Object Model) HTML, můžete také manipulovat s obsahem aktuální webové stránky prostřednictvím `Document` Vlastnosti. Pomocí této vlastnosti můžete místo navigace mezi soubory ukládat a upravovat dokumenty v paměti.  
  
 `Document`Vlastnost také umožňuje volat metody implementované ve skriptovacím kódu webové stránky z kódu klientské aplikace. Pro přístup ke kódu klientské aplikace z vašeho skriptovacího kódu nastavte `ObjectForScripting` vlastnost. K objektu, který zadáte, lze použít kód skriptu jako `window.external` objekt.  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A>majetek|Získává objekt, který poskytuje spravovaný přístup k objektovému modelu dokumentu HTML aktuální webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>událostí|Nastane, pokud se dokončí načítání webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A>majetek|Získá nebo nastaví obsah HTML aktuální webové stránky.|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A>majetek|Získá název aktuální webové stránky.|  
|Metoda <xref:System.Windows.Forms.WebBrowser.GoBack%2A>|Přejde na předchozí stránku v historii.|  
|Metoda <xref:System.Windows.Forms.WebBrowser.GoForward%2A>|Přejde na další stránku v historii.|  
|Metoda <xref:System.Windows.Forms.WebBrowser.Navigate%2A>|Přejde na zadanou adresu URL.|  
|<xref:System.Windows.Forms.WebBrowser.Navigating>událostí|Vyvolá se před zahájením navigace a povolí akci, která se má zrušit.|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A>majetek|Získá nebo nastaví objekt, který může kód skriptu webové stránky použít ke komunikaci s vaší aplikací.|  
|Metoda <xref:System.Windows.Forms.WebBrowser.Print%2A>|Vytiskne aktuální webovou stránku.|  
|Metoda <xref:System.Windows.Forms.WebBrowser.Refresh%2A>|Znovu načte aktuální webovou stránku.|  
|Metoda <xref:System.Windows.Forms.WebBrowser.Stop%2A>|Zastaví aktuální navigaci a zastaví dynamické prvky stránky, například zvuky a animace.|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A>majetek|Získá nebo nastaví adresu URL aktuální webové stránky. Nastavením této vlastnosti přejdete k ovládacímu prvku na novou adresu URL.|  
  
## <a name="see-also"></a>Viz také

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
- [Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Postupy: Tisk pomocí ovládacího prvku WebBrowser](how-to-print-with-a-webbrowser-control.md)
- [Postupy: Přidání schopností webového prohlížeče do aplikace Windows Forms](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [Postupy: Vytvoření prohlížeče dokumentu HTML v aplikaci Windows Forms](how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [Postupy: Implementace obousměrné komunikace mezi kódem DHTML a kódem klientské aplikace](implement-two-way-com-between-dhtml-and-client.md)
- [WebBrowser – zabezpečení](webbrowser-security.md)
