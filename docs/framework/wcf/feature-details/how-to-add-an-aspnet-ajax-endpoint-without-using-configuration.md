---
title: 'Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9aab53d6457aa7848fd4acea6317a30da352cc98
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579628"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje koncový bod s povoleným ASP.NET AJAX, který se dá volat z JavaScriptu na klientském webu. Chcete-li vytvořit takový koncový bod, můžete buď použít konfigurační soubor, stejně jako všechny ostatní koncové body WCF, nebo použít metodu, která nevyžaduje žádné konfigurační prvky. Toto téma ukazuje druhý přístup.  
  
 Chcete-li vytvořit služby s koncovými body ASP.NET AJAX bez konfigurace, musí být služby hostovány Internetová informační služba (IIS). Chcete-li aktivovat koncový bod ASP.NET AJAX pomocí tohoto přístupu, zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jako parametr Factory v direktivě [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) v souboru. svc. Tato vlastní továrna je komponenta, která automaticky konfiguruje koncový bod ASP.NET AJAX tak, aby jej bylo možné volat z JavaScriptu na klientském webu.  
  
 Pracovní příklad naleznete v tématu [Služba AJAX bez konfigurace](../samples/ajax-service-without-configuration.md).  
  
 Osnova, jak nakonfigurovat koncový bod ASP.NET AJAX pomocí elementů konfigurace, naleznete v tématu [How to: use Configuration to Add the ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Vytvoření základní služby WCF  
  
1. Definujte základní kontrakt služby WCF s rozhraním označeným <xref:System.ServiceModel.ServiceContractAttribute> atributem. Označte každou operaci pomocí <xref:System.ServiceModel.OperationContractAttribute> . Nezapomeňte nastavit <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. Implementujte `ICalculator` kontrakt služby s `CalculatorService` .  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. Definujte obor názvů pro `ICalculator` implementace a jejich `CalculatorService` zabalením do bloku oboru názvů.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Hostování služby v Internetová informační služba bez konfigurace  
  
1. V aplikaci vytvořte nový soubor s názvem služba s příponou. svc. Upravte tento soubor přidáním příslušné informace o direktivě [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) pro službu. Určete, že se má <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> použít v direktivě [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) k automatické konfiguraci koncového bodu ASP.NET AJAX.  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. Sestavte službu a zavolejte ji z klienta. Internetová informační služba (IIS) aktivuje službu při volání. Další informace o hostování ve službě IIS najdete v tématu [How to: Host a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Volání služby  
  
1. Koncový bod je nakonfigurován na prázdné adrese relativní vzhledem k souboru. svc, takže služba je nyní k dispozici a lze ji vyvolat odesláním požadavků do služby. svc/ \<operation> -například Service. svc/Add pro `Add` operaci. Můžete ji použít tak, že zadáte adresu URL služby do kolekce Scripts ovládacího prvku Správce skriptů ASP.NET AJAX. Příklad naleznete v tématu [Služba AJAX bez konfigurace](../samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Příklad  
  
 Automaticky konfigurovaný koncový bod se vytvoří na prázdné adrese relativní vzhledem k základní adrese URL. S tímto přístupem je možné taky přidat konfigurační soubor a použít ho. Pokud konfigurační soubor obsahuje definice koncových bodů, tyto koncové body se přidají do automaticky konfigurovaného koncového bodu.  
  
 Například služba. svc používá <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> a adresář služby obsahuje soubor Web. config, který definuje koncový bod pro stejnou službu pomocí na <xref:System.ServiceModel.BasicHttpBinding> relativní adrese "SOAP". V tomto případě služba obsahuje dva koncové body: jeden na Service. svc (který reaguje na požadavky ASP.NET AJAX) a druhý v Service. svc/SOAP (který reaguje na žádosti SOAP).  
  
 Pokud konfigurační soubor definuje koncový bod na prázdné relativní adrese a <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> použije se, vyvolá se výjimka a služba se nespustí.  
  
 Konfiguraci nelze použít pro úpravu nastavení automaticky konfigurovaného koncového bodu. Pokud je nutné změnit jakékoli nastavení (například kvótu čtenářů), nepoužívejte přístup k nebezplatné konfiguraci odebráním <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ze souboru. svc a vytvořením položky konfigurace pro koncový bod.  
  
 Pokud vaše služba vyžaduje režim kompatibility ASP.NET, například pokud používá <xref:System.Web.HttpContext> autorizační mechanismy třídy nebo ASP.NET, je pro zapnutí tohoto režimu stále nutný konfigurační soubor. Požadovaný prvek konfigurace je [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) element, který musí být přidán následujícím způsobem.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Další informace najdete v tématu [služby WCF a ASP.NET](wcf-services-and-aspnet.md) .  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>Třída je odvozenou třídou třídy <xref:System.ServiceModel.Activation.ServiceHostFactory> . Podrobné vysvětlení mechanismu výrobního hostitele služby najdete v tématu [rozšíření hostování pomocí ServiceHostFactory](../extending/extending-hosting-using-servicehostfactory.md) .  
  
## <a name="see-also"></a>Viz také

- [Vytváření služeb WCF pro ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md)
- [Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
