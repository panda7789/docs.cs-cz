---
title: Ukázka samostatného diagnostického informačního kanálu
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: c8a64c209711734b4915f332e9242346e295ddea
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417046"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Ukázka samostatného diagnostického informačního kanálu
Tato ukázka předvádí, jak vytvořit informační kanál RSS/Atom pro syndikaci pomocí Windows Communication Foundation (WCF). Jedná se o základní program "Hello World", který ukazuje základy objektového modelu a jak ho nastavit ve službě Windows Communication Foundation (WCF).  
  
 Modely WCF: informační kanály syndikace jako operace služby, které vracejí speciální datový typ, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Instance <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> mohou serializovat informační kanál do formátů RSS 2,0 a Atom 1,0. Následující vzorový kód ukazuje použití smlouvy.  
  
```csharp  
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
  
 Operace `GetProcesses` je označena atributem <xref:System.ServiceModel.Web.WebGetAttribute>, který umožňuje řídit, jak služba WCF odesílá požadavky HTTP GET na operace služby a určuje formát odeslaných zpráv.  
  
 Podobně jako u libovolné služby WCF se můžou informační kanály syndikace hostovat sami v jakékoli spravované aplikaci. Služba syndikace vyžaduje konkrétní vazbu (<xref:System.ServiceModel.WebHttpBinding>) a specifické chování koncového bodu (<xref:System.ServiceModel.Description.WebHttpBehavior>), aby fungovalo správně. Nová třída <xref:System.ServiceModel.Web.WebServiceHost> poskytuje pohodlný rozhraní API pro vytváření takových koncových bodů bez konkrétní konfigurace.  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Alternativně můžete použít <xref:System.ServiceModel.Activation.WebServiceHostFactory> ze souboru hostovaného v rámci služby IIS k poskytnutí ekvivalentních funkcí (Tato technika není znázorněna v tomto ukázkovém kódu).  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 Vzhledem k tomu, že tato služba přijímá žádosti pomocí standardního HTTP GET, můžete k přístupu ke službě použít libovolného klienta využívajícího technologii RSS nebo ATOM. Výstup této služby můžete například zobrazit tak, že přejdete na `http://localhost:8000/diagnostics/feed/?format=atom` nebo `http://localhost:8000/diagnostics/feed/?format=rss` v prohlížeči podporujícím technologii RSS.
  
 Můžete také použít způsob, [jakým objektový model Syndikace WCF mapuje na Atom a RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) pro čtení publikovaných dat a jejich zpracování pomocí imperativního kódu.  
  
```csharp  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že máte v počítači správné oprávnění k registraci adres pro HTTP a HTTPS, jak je vysvětleno v postupu nastavení v části Postup nastavení v [Windows Communication Foundationch ukázkách](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Sestavte řešení.  
  
3. Spusťte konzolovou aplikaci.  
  
4. Když je spuštěná Konzolová aplikace, přejděte do `http://localhost:8000/diagnostics/feed/?format=atom` nebo `http://localhost:8000/diagnostics/feed/?format=rss` pomocí prohlížeče podporujícího technologii RSS.  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>Viz také:

- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
