---
title: Ukázka samostatného diagnostického informačního kanálu
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 2737621a98f6a7e89ef3aee01fd1ad7a2a60f9b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316554"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Ukázka samostatného diagnostického informačního kanálu
Tento příklad ukazuje, jak vytvořit pro syndikaci Windows Communication Foundation (WCF) informační kanál RSS/Atom. Je to základní program "Hello World", který ukazuje základy objektový model a jak ho nastavit na službu Windows Communication Foundation (WCF).  
  
 WCF modely jako servisní operace, které vracejí zvláštní datový typ, informační kanály syndikace <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Instance <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> může serializovat informačního kanálu do formátů RSS 2.0 a Atom 1.0. Následující ukázkový kód ukazuje kontrakt použít.  
  
```  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.   
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 `GetProcesses` Operace je opatřen poznámkou <xref:System.ServiceModel.Web.WebGetAttribute> k operacím služby a určení formátu zpráv odeslaných požadavků atribut, který vám umožňuje řídit, jak WCF odešle HTTP GET.  
  
 Stejně jako libovolnou službu WCF může být informační kanály syndikace vlastní hostované v žádné spravované aplikace. Syndikace služby vyžadují konkrétní vazbu ( <xref:System.ServiceModel.WebHttpBinding>) a chování určitého koncového bodu ( <xref:System.ServiceModel.Description.WebHttpBehavior>) fungovala správně. Nové <xref:System.ServiceModel.Web.WebServiceHost> třída poskytuje pohodlné rozhraní API pro vytváření těchto koncových bodů bez určitou konfiguraci.  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternativně můžete použít <xref:System.ServiceModel.Activation.WebServiceHostFactory> z v rámci souboru .svc hostované službou IIS ekvivalentní nakonfigurovánu (Tento postup není ukázáno v tomto ukázkovém kódu).  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 Protože tato služba přijímá požadavky pomocí standardní HTTP GET, můžete použít libovolného klienta RSS nebo s ohledem na ATOM pro přístup ke službě. Například můžete zobrazit výstup této služby tak, že přejdete do `http://localhost:8000/diagnostics/feed/?format=atom` nebo `http://localhost:8000/diagnostics/feed/?format=rss` v prohlížeči podporující RSS.
  
 Můžete také použít [jak the WCF syndikace objektu modelu mapuje na Atom a RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) syndikovaný data číst a zpracovat je pomocí imperativního kódu.  
  
```  
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",  
new XmlReaderSettings()  
{  
//MaxCharactersInDocument can be used to control the maximum amount of data   
//read from the reader and helps prevent OutOfMemoryException  
MaxCharactersInDocument = 1024 * 64  
} );  
  
SyndicationFeed feed = SyndicationFeed.Load( reader );  
  
foreach (SyndicationItem i in feed.Items)  
{  
        XmlSyndicationContent content = i.Content as XmlSyndicationContent;  
        ProcessData pd = content.ReadContent<ProcessData>();  
  
        Console.WriteLine(i.Title.Text);  
        Console.WriteLine(pd.ToString());  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že máte oprávnění registrace správné adresy pro protokol HTTP a HTTPS v počítači, jak je vysvětleno v nastavení podle pokynů v [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Sestavte řešení.  
  
3. Spusťte konzolovou aplikaci.  
  
4. Je spuštěn konzolovou aplikaci, přejděte na `http://localhost:8000/diagnostics/feed/?format=atom` nebo `http://localhost:8000/diagnostics/feed/?format=rss` pomocí prohlížeče podporující RSS.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>Viz také:

- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
