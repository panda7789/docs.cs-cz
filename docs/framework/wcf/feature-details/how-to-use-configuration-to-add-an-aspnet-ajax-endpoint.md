---
title: 'Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 97f8174161068f2c72b6bd2bc4e8a3044f5bccdd
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051659"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zpřístupňuje koncový bod s povoleným ASP.NET AJAX, který lze volat z JavaScriptu na klientském webu. Chcete-li vytvořit takový koncový bod, můžete buď použít konfigurační soubor, stejně jako všechny ostatní koncové body služby Windows Communication Foundation (WCF), nebo použít metodu, která nevyžaduje žádné konfigurační prvky. Toto téma ukazuje přístup ke konfiguraci.  
  
 Část postupu umožňující, aby se koncový bod služby stal ASP.NET AJAX, se skládá z konfigurace koncového bodu pro použití <xref:System.ServiceModel.WebHttpBinding> a k přidání [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) chování koncového bodu. Po nakonfigurování koncového bodu jsou kroky pro implementaci a hostování služby podobné těm, které používá jakákoli služba WCF. Pracovní příklad naleznete v tématu [Služba AJAX pomocí HTTP POST](../samples/ajax-service-using-http-post.md).  
  
 Další informace o tom, jak nakonfigurovat koncový bod ASP.NET AJAX bez použití konfigurace, najdete v tématu [How to: Add a ASP.NET AJAX Endpoint bez použití Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
## <a name="to-create-a-basic-wcf-service"></a>Vytvoření základní služby WCF  
  
1. Definujte základní kontrakt služby WCF s rozhraním označeným <xref:System.ServiceModel.ServiceContractAttribute> atributem. Označte každou operaci pomocí <xref:System.ServiceModel.OperationContractAttribute> . Nezapomeňte nastavit <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
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
        // Other operations omitted…
    }
    ```  
  
3. Definujte obor názvů pro `ICalculator` implementace a jejich `CalculatorService` zabalením do bloku oboru názvů.  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Vytvoření koncového bodu ASP.NET AJAX pro službu  
  
1. Vytvořte konfiguraci chování a určete [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) chování pro koncové body služby s povoleným ASP.NET AJAX.  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. Vytvořte koncový bod pro službu, která používá <xref:System.ServiceModel.WebHttpBinding> chování nástroje a rozhraní ASP.NET AJAX definované v předchozím kroku.  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>
    ```  
  
## <a name="to-host-the-service-in-iis"></a>Hostování služby ve službě IIS  
  
1. Pokud chcete službu hostovat ve službě IIS, vytvořte v aplikaci nový soubor s názvem služba s příponou. svc. Upravte tento soubor přidáním příslušné informace o direktivě [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) pro službu. Například obsah v souboru služby pro `CalculatorService` ukázku obsahuje následující informace.  
  
    ```aspx-csharp
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. Další informace o hostování ve službě IIS najdete v tématu [How to: Host a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="to-call-the-service"></a>Volání služby  
  
1. Koncový bod je nakonfigurován na prázdné adrese relativní vzhledem k souboru. svc, takže služba je nyní k dispozici a lze ji vyvolat odesláním požadavků do služby. svc/ \<operation> -například Service. svc/Add pro `Add` operaci. Můžete ji použít tak, že zadáte adresu URL koncového bodu do kolekce Scripts ovládacího prvku Správce skriptů ASP.NET AJAX. Příklad najdete v tématu [Služba AJAX pomocí HTTP POST](../samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Viz také

- [Vytváření služeb WCF pro ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md)
- [Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
