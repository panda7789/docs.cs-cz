---
title: "Ukázka samostatného diagnostického informačního kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7cf6bb08dc6607bf6c5b9e283ce449b603cb38d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Ukázka samostatného diagnostického informačního kanálu
Tento příklad ukazuje postup vytvoření informačního kanálu RSS nebo kanálu Atom pro syndikace s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Je základní program "Hello World", který ukazuje základy objektový model a jak nastavit na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]modely jako operace služby, které vracejí speciální datového typu, informační kanály syndikace <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Instance <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> může serializovat informačního kanálu do formátů, jak technologie RSS 2.0 a Atom 1.0. Následující vzorový kód ukazuje kontrakt použít.  
  
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
  
 `GetProcesses` Je opatřen poznámkou operaci <xref:System.ServiceModel.Web.WebGetAttribute> atribut, který umožňuje určit jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odešle zprávu žádosti HTTP GET na služby operations a zadejte formát zprávy odeslané.  
  
 Jako žádné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, informační kanály syndikace může být sám sebou hostované ve všech spravovaných aplikací. Syndikace služby vyžadují konkrétní vazbu ( <xref:System.ServiceModel.WebHttpBinding>) a chování konkrétní koncový bod ( <xref:System.ServiceModel.Description.WebHttpBehavior>) fungovat správně. Nové <xref:System.ServiceModel.Web.WebServiceHost> třída poskytuje pohodlné rozhraní API pro vytváření těchto koncových bodů bez konkrétní konfigurace.  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternativně můžete použít <xref:System.ServiceModel.Activation.WebServiceHostFactory> z v rámci soubor hostované službou IIS SVC ekvivalentní nakonfigurovánu (Tento postup není ukázáno v ukázkový kód).  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 Protože tato služba přijímá požadavky pomocí standardní HTTP GET, můžete použít libovolného klienta RSS nebo ATOM podporující přístup ke službě. Například můžete zobrazit výstup této služby přechodem na http://localhost: 8000/diagnostiky nebo informační kanál /? formátu =, nebo http://localhost: 8000/diagnostiky nebo informační kanál atom /? formátu = rss v prohlížeči sítě podporující RSS, jako je například Internet Explorer 7.  
  
 Můžete také [jak WCF syndikace objektu modelu mapy na Atom a RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) ke čtení syndikovaný dat a zpracování pomocí imperativní kódu.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, zda máte oprávnění registrace správné adresy pro protokol HTTP a HTTPS v počítači, jak je popsáno v nastavení podle pokynů [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení.  
  
3.  Spusťte konzolovou aplikaci.  
  
4.  Je spuštěn konzolové aplikace, přejděte na http://localhost: 8000/diagnostiky nebo informační kanál /? formátu =, nebo http://localhost: 8000/diagnostiky nebo informační kanál atom /? formátu = rss pomocí podporující RSS prohlížeče.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>Viz také  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
