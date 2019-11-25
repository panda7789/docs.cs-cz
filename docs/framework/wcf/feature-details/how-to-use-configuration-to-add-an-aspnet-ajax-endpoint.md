---
title: 'Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 3ccfb34614707c17885da3ed37f545bbab808869
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978270"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zpřístupňuje koncový bod s povoleným ASP.NET AJAX, který lze volat z JavaScriptu na klientském webu. Chcete-li vytvořit takový koncový bod, můžete buď použít konfigurační soubor, stejně jako všechny ostatní koncové body služby Windows Communication Foundation (WCF), nebo použít metodu, která nevyžaduje žádné konfigurační prvky. Toto téma ukazuje přístup ke konfiguraci.  
  
 Část postupu umožňující, aby se koncový bod služby stal ASP.NET AJAX, se skládá z konfigurace koncového bodu pro použití <xref:System.ServiceModel.WebHttpBinding> a přidání [\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) koncového bodu. Po nakonfigurování koncového bodu jsou kroky pro implementaci a hostování služby podobné těm, které používá jakákoli služba WCF. Pracovní příklad naleznete v tématu [Služba AJAX pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Další informace o tom, jak nakonfigurovat koncový bod ASP.NET AJAX bez použití konfigurace, najdete v tématu [How to: Add a ASP.NET AJAX Endpoint bez použití Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
## <a name="to-create-a-basic-wcf-service"></a>Vytvoření základní služby WCF  
  
1. Definujte základní kontrakt služby WCF s rozhraním označeným atributem <xref:System.ServiceModel.ServiceContractAttribute>. Označte každou operaci pomocí <xref:System.ServiceModel.OperationContractAttribute>. Nezapomeňte nastavit vlastnost <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.  
  
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
  
2. Implementujte kontrakt služby `ICalculator` pomocí `CalculatorService`.  
  
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
  
3. Definujte obor názvů pro `ICalculator` a `CalculatorService` implementace jejich zabalením do bloku oboru názvů.  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Vytvoření koncového bodu ASP.NET AJAX pro službu  
  
1. Vytvořte konfiguraci chování a určete\<chování [> enableWebScript](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) pro koncové body služby s povoleným AJAX ASP.NET.  
  
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
  
2. Vytvořte koncový bod pro službu, která používá <xref:System.ServiceModel.WebHttpBinding> a chování AJAX ASP.NET definované v předchozím kroku.  
  
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
  
1. Pokud chcete službu hostovat ve službě IIS, vytvořte v aplikaci nový soubor s názvem služba s příponou. svc. Upravte tento soubor přidáním příslušné informace o direktivě [ServiceHost\@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) pro tuto službu. Například obsah v souboru služby pro ukázku `CalculatorService` obsahuje následující informace.  
  
    ```
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. Další informace o hostování ve službě IIS najdete v tématu [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="to-call-the-service"></a>Volání služby  
  
1. Koncový bod je nakonfigurován na prázdné adrese relativní vzhledem k souboru. svc, takže služba je nyní k dispozici a je možné ji vyvolat odesláním žádostí do operace Service. svc/\<>-například Service. svc/Add pro `Add` operace. Můžete ji použít tak, že zadáte adresu URL koncového bodu do kolekce Scripts ovládacího prvku Správce skriptů ASP.NET AJAX. Příklad najdete v tématu [Služba AJAX pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Viz také:

- [Vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Postupy: Migrace webových služeb ASP.NET s podporou AJAX na WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
