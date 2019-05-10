---
title: Koncové body SOAP a HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: c07391ccd1f8db6e5d2cb6e0c24fc06152d7517f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617519"
---
# <a name="soap-and-http-endpoints"></a>Koncové body SOAP a HTTP
Tento příklad ukazuje, jak implementovat službu vzdáleného volání procedur a zpřístupnit ji ve formátu protokolu SOAP a ve formátu "Plain Old XML" (POX) s využitím modelu webového programování WCF. Zobrazit [základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) ukázka podrobné informace o vazbě protokolu HTTP pro službu. Tato ukázka se zaměřuje na informace, které se týkají vystavení stejnou službu SOAP a HTTP pomocí různých vazeb.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vystavení služby RPC přes protokol SOAP a HTTP pomocí technologie WCF.  
  
## <a name="discussion"></a>Diskuse  
 Tato ukázka obsahuje dvě součásti: projekt webové aplikace (služba), která obsahuje službu WCF a Konzolová aplikace (klient), která volá operace služby pomocí vazby protokolu SOAP a HTTP.  
  
 Služba WCF poskytuje 2 činnosti`GetData` a `PutData` –, který echo řetězec, který byl předán jako vstup. Operace služby jsou opatřeny poznámkami s <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute>. Tyto atributy řídí projekce HTTP z těchto operací. Kromě toho jsou označena s <xref:System.ServiceModel.OperationContractAttribute>, což umožňuje jim být vystaveno přes vazby SOAP. Služby `PutData` vyvolá metoda výjimku <xref:System.ServiceModel.Web.WebFaultException>, která se odesílá zpět prostřednictvím protokolu HTTP stavový kód HTTP a odeslán zpět přes protokol SOAP jako chybu protokolu SOAP.  
  
 V souboru Web.config Konfiguruje službu WCF s 3 koncové body:  
  
- ~/Service.svc/mex koncového bodu, který zveřejňuje metadata služby pro přístup založený na protokolu SOAP klienty.  
  
- ~/Service.svc/http koncového bodu, který umožňuje klientům přístup ke službě pomocí vazby HTTP.  
  
- Koncový bod ~/service.svc/soap, která umožňuje klientům přístup ke službě pomocí SOAP přes vazbu protokolu HTTP.  
  
 Koncový bod HTTP, nastavena <`webHttp`> standardní koncový bod, který má `helpEnabled` nastavena na `true`. V důsledku toho služba zpřístupňuje stránku nápovědy na základě XHTML ~/service.svc/http/help, založené na protokolu HTTP klientů můžete použít pro přístup ke službě.  
  
 Klientský projekt ukazuje přístupu ke službě pomocí proxy serveru SOAP (vygenerované pomocí **přidat odkaz na službu**) a přístup pomocí služby <xref:System.Net.WebClient>.  
  
 Ukázka se skládá z hostované webové služby a aplikace konzoly. Konzolová aplikace běží, klient vytvářejí požadavky na službu a zapíše relevantní informace z odpovědi v okně konzoly.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1. Otevřete řešení pro Ukázka koncové body HTTP a protokolu SOAP.  
  
2. Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
3. Pokud ho ještě není otevřený, stiskněte kombinaci kláves CTRL + W, S otevřete **Průzkumníka řešení** okna.  
  
4. Z **Průzkumníku řešení** okna, klikněte pravým tlačítkem na **služby** projektu a umístěte kurzor **ladění** možnost místní nabídky tak, aby **spustit nový Instance** se zobrazí místní nabídka. Klikněte na tlačítko **spustit novou instanci**. Tím se spustí serveru ASP.NET development server, který je hostitelem služby.  
  
5. Z okna Průzkumníka řešení, klikněte pravým tlačítkem na projekt klienta a umístěte kurzor **ladění** možnost místní nabídky tak, aby **spustit novou instanci** se zobrazí místní nabídka. Klikněte na tlačítko **spustit novou instanci**.  
  
6. V okně konzoly klienta se zobrazí a poskytuje URI spuštěnou službu a identifikátor URI HTML stránka pro spuštěnou službu nápovědy. Na stránce nápovědy HTML v libovolném bodě v čase zobrazíte tak, že zadáte identifikátor URI na stránce nápovědy v prohlížeči.  
  
7. Při spuštění ukázky klienta zapíše stavu aktuální aktivity.  
  
8. Stisknutím libovolné klávesy ukončete konzolovou aplikaci klienta.  
  
9. Stiskněte SHIFT + F5 ukončete ladění služby.  
  
10. V oznamovací oblasti Windows, klikněte pravým tlačítkem na ikonu ASP.NET development server a vyberte **Zastavit** v místní nabídce.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
