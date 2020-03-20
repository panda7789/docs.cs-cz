---
title: 'Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 5314bb000371ee2d3eef2576e1edfa455aa65b90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184839"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zpřístupňuje koncový bod s podporou ASP.NET AJAX, který lze volat z jazyka JavaScript na klientském webu. Chcete-li vytvořit takový koncový bod, můžete buď použít konfigurační soubor, stejně jako u všech ostatních koncových bodů Windows Communication Foundation (WCF), nebo použít metodu, která nevyžaduje žádné konfigurační prvky. Toto téma ukazuje přístup konfigurace.  
  
 Část postupu, který umožňuje koncový bod služby, aby se stal ASP.NET možnost ajax <xref:System.ServiceModel.WebHttpBinding> spočívá v konfiguraci koncového bodu pro použití a přidat [ \<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování koncového bodu. Po konfiguraci koncového bodu jsou kroky k implementaci a hostování služby podobné těm, které používá jakákoli služba WCF. Pracovní příklad naleznete v tématu [služba AJAX pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Další informace o konfiguraci koncového bodu ASP.NET AJAX bez použití konfigurace naleznete v [tématu How to: Add a ASP.NET koncový bod AJAX bez použití konfigurace](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
## <a name="to-create-a-basic-wcf-service"></a>Vytvoření základní služby WCF  
  
1. Definujte základní servisní smlouvu WCF <xref:System.ServiceModel.ServiceContractAttribute> s rozhraním označeným atributem. Každou operaci označte pomocí <xref:System.ServiceModel.OperationContractAttribute>. Nezapomeňte nastavit <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.  
  
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
  
2. Dokončujte `ICalculator` `CalculatorService`servisní smlouvu s .  
  
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
  
3. Definujte obor názvů `ICalculator` `CalculatorService` pro a implementace zabalením do bloku oboru názvů.  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Vytvoření ASP.NET koncového bodu AJAX pro službu  
  
1. Vytvořte konfiguraci chování a určete [ \<chování enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) pro koncové body služby s podporou ASP.NET AJAX.  
  
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
  
2. Vytvořte koncový bod pro službu, která používá <xref:System.ServiceModel.WebHttpBinding> a a chování AJAX ASP.NET definované v předchozím kroku.  
  
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
  
1. Chcete-li službu hostovat ve službě IIS, vytvořte v aplikaci nový soubor s názvem service s příponou SVC. Upravte tento soubor [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) přidáním příslušných informací směrnice ServiceHost pro službu. Například obsah v souboru služby pro ukázku `CalculatorService` obsahuje následující informace.  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. Další informace o hostování ve službě IIS naleznete v [tématu How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="to-call-the-service"></a>Chcete-li volat službu  
  
1. Koncový bod je konfigurován na prázdnou adresu vzhledem k souboru .svc, takže služba je nyní k dispozici\<a může být vyvolána odesláním požadavků `Add` na service.svc/ operace> - například service.svc/Add pro operaci. Můžete jej použít zadáním adresy URL koncového bodu do kolekce Skripty ovládacího prvku ASP.NET Ajax Script Manager. Příklad naleznete v tématu [služba AJAX pomocí protokolu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Viz také

- [Vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
