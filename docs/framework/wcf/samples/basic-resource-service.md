---
title: Služba základních prostředků
ms.date: 03/30/2017
ms.assetid: 4360063e-cc8c-4648-846e-c05a5af51a7a
ms.openlocfilehash: 2d55aecfdf6579b1de4c0cc324e59e23c251b12d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520133"
---
# <a name="basic-resource-service"></a>Služba základních prostředků
Tento příklad ukazuje, jak implementovat nějakou službu založenou na protokolu HTTP pomocí Windows Communication Foundation (WCF) REST programovacího modelu, který poskytuje kolekci zákazníků, který podporuje načtení, přidat, odstranit a nahrazovat operace. Tento příklad se skládá z 2 komponenty – v místním prostředí služby WCF HTTP (Service.cs) a Konzolová aplikace (program.cs), který vytvoří službu a provede volání do něj.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Služba WCF poskytuje kolekci zákazníků způsobem resource orientované nebo rozhraní REST. Stručně řečeno to je občas jedinečné identifikátory URI pro kolekci zákazníků a každý zákazník v kolekci. Tato služba podporuje odesílání HTTP `GET` na identifikátor URI a získejte celou kolekci a HTTP kolekce `POST` na identifikátor URI pro přidání nového zákazníka ke kolekci kolekce. Také v identifikátoru URI pro individuálního zákazníka, podporuje HTTP `GET` zákazník získat tak podrobné údaje, HTTP `PUT` nahradit podrobnosti zákazníka a HTTP `DELETE` odebrání zákazníka z kolekce. Při přidání nového zákazníka ke kolekci, služba ho přiřadí jedinečný identifikátor URI a ukládá identifikátoru URI jako součást podrobnosti zákazníka. Také komunikuje identifikátoru URI pomocí HTTP umístění hlavičky odpovědi klientovi.  
  
 Soubor App.config Konfiguruje službu WCF s výchozím <xref:System.ServiceModel.Description.WebHttpEndpoint> , který má <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> nastavenou na `true`. V důsledku toho WCF vytvoří automatickou založený na jazyce HTML stránku nápovědy na `http://localhost:8000/Customers/help` , který poskytuje informace o tom, jak vytvořit HTTP žádostí o služby a jak získat přístup k služby odpověď HTTP – třeba příklad, jak se podrobnosti o zákazníkovi vyjádřena v XML a JSON.  
  
 Vystavení kolekcí zákazníků (a obecněji prostředek) tímto způsobem umožňuje pracovat s ním jednotným způsobem pomocí identifikátorů URI a HTTP klientovi `GET`, `PUT`, `DELETE` a `POST`. Soubor program.cs ukazuje, jak tohoto klienta lze vytvořené využitím <xref:System.Net.HttpWebRequest>. Všimněte si, že toto je pouze jeden způsob, jak získat přístup ke službě WCF REST. Je také možné získat přístup ke službě pomocí ostatních tříd rozhraní .NET Framework, jako <xref:System.ServiceModel.ChannelFactory> a <xref:System.Net.WebClient>. Další ukázky v sadě SDK (například [základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) ukázky a [automatický výběr formátu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) ukázkové) ukazují, jak použít tyto třídy komunikovat se službou WCF.  
  
 Ukázka obsahuje služba v místním prostředí a klient i spuštění v rámci konzolové aplikace. Konzolová aplikace běží, klient vytvářejí požadavky na službu a zapíše relevantní informace z odpovědi v okně konzoly.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení pro základní Ukázka služby prostředků. Při spuštění [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], musíte spustit jako správce pro ukázku proběhl úspěšně. To můžete provést kliknutím pravým tlačítkem myši [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonu a vyberete **spustit jako správce** v místní nabídce.  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, sestavte řešení a potom stiskněte klávesu Ctrl + F5 ke spuštění aplikace konzoly. V okně konzoly se zobrazí a poskytuje URI spuštěnou službu a stránku pro spuštěnou službu identifikátoru URI HTML s nápovědou. Na stránce nápovědy HTML v libovolném bodě v čase zobrazíte tak, že zadáte identifikátor URI na stránce nápovědy v prohlížeči. Při spuštění ukázky klienta zapíše stavu aktuální aktivity.  
  
3.  Stisknutím libovolné klávesy ukončete vzorovou.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicResourceService`  
  
## <a name="see-also"></a>Viz také  
 [Základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md)  
 [Automatický výběr formátu](../../../../docs/framework/wcf/samples/automatic-format-selection.md)
