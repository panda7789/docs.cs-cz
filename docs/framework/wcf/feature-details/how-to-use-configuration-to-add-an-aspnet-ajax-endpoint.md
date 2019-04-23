---
title: 'Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: db5085d01dbed841109ac46fe4e8b2a0143352e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337614"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která umožňuje použití technologie ASP.NET AJAX koncový bod k dispozici, který může být volána z jazyka JavaScript na webové stránce klienta. Vytvořit takové koncový bod, můžete použít konfigurační soubor, stejně jako všechny ostatní koncové body Windows Communication Foundation (WCF) nebo používat metodu, která nevyžaduje žádné konfigurační prvky. Toto téma popisuje postup konfigurace.  
  
 Součást procesu, který umožňuje koncový bod služby se podporou technologie ASP.NET AJAX se skládá z konfigurace koncového bodu pro použití <xref:System.ServiceModel.WebHttpBinding> a přidat [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování koncového bodu. Po dokončení konfigurace koncového bodu, kroky pro implementaci služby hostování jsou podobné těm, které jsou používané libovolnou službu WCF. Funkční příklad najdete v článku [AJAX služba využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Další informace týkající se konfigurace koncového bodu ASP.NET AJAX bez použití konfigurace najdete v tématu [jak: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Chcete-li vytvořit základní služby WCF  
  
1. Definování základní kontraktu služby WCF s rozhraním označené <xref:System.ServiceModel.ServiceContractAttribute> atribut. Označit každou operaci s <xref:System.ServiceModel.OperationContractAttribute>. Nezapomeňte nastavit <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.  
  
    ```  
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. Implementace `ICalculator` kontrakt služby s `CalculatorService`.  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. Definování oboru názvů pro `ICalculator` a `CalculatorService` implementace obalením v oboru bloku.  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Vytvoření koncového bodu ASP.NET AJAX pro služby  
  
1. Vytvořte konfiguraci chování a zadejte [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování při použití technologie ASP.NET AJAX koncových bodů služby.  
  
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
  
2. Vytvoření koncového bodu služby, který používá <xref:System.ServiceModel.WebHttpBinding> a ASP.NET AJAX chování definované v předchozím kroku.  
  
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
  
### <a name="to-host-the-service-in-iis"></a>K hostování služby ve službě IIS  
  
1. K hostování služby ve službě IIS, vytvořte nový soubor s názvem služby s příponou .svc v aplikaci. Tento soubor upravit tak, že přidáte odpovídající [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktiv informace pro službu. Například obsah do souboru definice služby pro `CalculatorService` vzorek obsahuje následující informace.  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. Další informace o hostování ve službě IIS najdete v tématu [jak: Hostování služby WCF v IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Volání služby  
  
1. Koncový bod je nakonfigurována na prázdnou adresu relativní k souboru .svc tak, aby služba je nyní k dispozici a lze vyvolat pomocí zasílání požadavků na service.svc/\<operace > – například service.svc/Add pro `Add` operace. Můžete ho tak, že zadáte adresu URL koncového bodu do kolekce skriptů ovládací prvek správce skriptů ASP.NET AJAX. Příklad najdete v tématu [AJAX služba využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Viz také:

- [Vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Postupy: Migrace s povoleným AJAX webových služeb ASP.NET na WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
