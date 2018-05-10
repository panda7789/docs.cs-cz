---
title: Koncové body SOAP a HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: 4c8a4695dbcaee2f0e7584418fbeac12815fa967
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="soap-and-http-endpoints"></a>Koncové body SOAP a HTTP
Tento příklad znázorňuje způsob implementace služby vzdáleného volání procedur a vystavit ve formátu protokolu SOAP a formát "Prostý formát XML" (POX) pomocí modelu programování WCF Web. Najdete v článku [základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) ukázku další podrobnosti o vazby HTTP pro službu. Tato ukázka se zaměřuje na podrobnosti, které se vztahují k vystavení stejnou službu prostřednictvím protokolu SOAP a HTTP pomocí různých vazeb.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vystavení služby RPC prostřednictvím protokolu SOAP a HTTP pomocí WCF.  
  
## <a name="discussion"></a>Diskusní  
 Tato ukázka se skládá ze dvou komponent: projektu webové aplikace (služba), který obsahuje službu WCF a konzolové aplikace (klient), která volá operací služby pomocí vazby protokolu SOAP a HTTP.  
  
 Služby WCF zpřístupní 2 operations –`GetData` a `PutData` – které odezvu řetězec, který byl předán jako vstup. Operace služby jsou opatřen poznámkou <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute>. Tyto atributy řídit projekce HTTP z těchto operací. Kromě toho jsou opatřen poznámkou <xref:System.ServiceModel.OperationContractAttribute>, což umožňuje jejich mají být exponovány přes vazby protokolu SOAP. Služby `PutData` metoda vrátí <xref:System.ServiceModel.Web.WebFaultException>, která se odešlou zpět přes protokol HTTP pomocí stavový kód HTTP a je odeslán zpět přes protokol SOAP jako chyba protokolu SOAP.  
  
 V souboru Web.config Konfiguruje službu WCF s 3 koncové body:  
  
-   ~/Service.svc/mex koncového bodu, který zveřejňuje metadata služby pro přístup založený na protokolu SOAP klienty.  
  
-   ~/Service.svc/http koncového bodu, který umožňuje klientům přístup ke službě pomocí vazby HTTP.  
  
-   ~/Service.svc/soap koncového bodu, který umožňuje klientům přístup ke službě pomocí SOAP přes vazby HTTP.  
  
 Koncový bod HTTP nastavena <`webHttp`> standardní koncový bod, který má `helpEnabled` nastavena na `true`. V důsledku toho služba zpřístupní stránku XHTML na základě nápovědy na ~/service.svc/http/help používaných klienty založené na protokolu HTTP k přístupu ke službě.  
  
 Projektu klienta ukazuje přístupu ke službě pomocí serveru proxy protokolu SOAP (vygenerované pomocí **přidat odkaz na službu**) a přístup pomocí služby <xref:System.Net.WebClient>.  
  
 Ukázka se skládá z hostované webové služby a aplikace konzoly. Konzolové aplikace běží, klient odešle žádosti o službu a zapisuje příslušné informace z odpovědi do okna konzoly.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení pro protokolu SOAP a ukázkové koncových bodů protokolu HTTP.  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
3.  Pokud již není otevřený, stiskněte CTRL + W, S otevřete **Průzkumníku řešení** okno.  
  
4.  Z **Průzkumníku řešení** okno, klikněte pravým tlačítkem myši **služby** projektu a umístěte kurzor myši **ladění** možnost místní nabídky tak, aby **spustit nový Instance** Kontextová nabídka se zobrazí. Klikněte na tlačítko **spustit novou instanci**. Spustí vývojový server ASP.NET, který hostuje službu.  
  
5.  Z okna Průzkumníku řešení klikněte pravým tlačítkem na projekt klienta a umístěte kurzor přes **ladění** možnost místní nabídky, aby **spustit novou instanci** Kontextová nabídka se zobrazí. Klikněte na tlačítko **spustit novou instanci**.  
  
6.  V okně konzoly klienta se zobrazí a poskytuje identifikátor URI spuštěné služby a identifikátor URI HTML stránka pro spuštěnou službu nápovědy. V libovolném bodě v čase můžete zobrazit na stránce nápovědy HTML zadáním identifikátor URI stránky nápovědy v prohlížeči.  
  
7.  Ukázka běží, zapíše klienta stavu aktuální aktivity.  
  
8.  Stisknutím libovolné klávesy ukončit klientská aplikace konzoly.  
  
9. Stisknutím klávesy SHIFT + F5 ukončete ladění služby.  
  
10. V oznamovací oblasti systému Windows klikněte pravým tlačítkem na ikonu ASP.NET development server a vyberte **Zastavit** v místní nabídce.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
