---
title: 'Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 28051dbed626dc0073a38e72f2cdc21ea108a32e
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Umožňuje vytvořit službu, která umožňuje použití ASP.NET AJAX koncový bod k dispozici, které lze volat z jazyka JavaScript na webovém serveru klienta. Pokud chcete vytvořit takové koncový bod, můžete použít buď konfigurační soubor s jiných [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] koncových bodů, nebo použijte metodu, která nevyžaduje, aby všechny konfigurace – elementy. Toto téma popisuje postup konfigurace.  
  
 V části procedury, která umožňuje koncovému bodu služby k použití ASP.NET AJAX je konfigurace koncového bodu používat <xref:System.ServiceModel.WebHttpBinding> a přidat [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování koncového bodu. Po dokončení konfigurace koncového bodu, jsou podobné těm, které jsou použity žádné kroky pro implementaci a hostitelem služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. Příklad pracovní najdete v tématu [AJAX služby pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Další informace o konfiguraci koncového bodu ASP.NET AJAX bez použití konfigurace najdete v tématu [postupy: Přidání aplikace ASP.NET AJAX konfigurace koncového bodu bez pomocí](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Chcete-li vytvořit základní služby WCF  
  
1.  Zadejte základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt služby s rozhraním označené jako <xref:System.ServiceModel.ServiceContractAttribute> atribut. Označit každou operaci s <xref:System.ServiceModel.OperationContractAttribute>. Nastavte <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.  
  
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
  
2.  Implementace `ICalculator` kontrakt služby s `CalculatorService`.  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  Zadejte obor názvů pro `ICalculator` a `CalculatorService` implementace podle jejich zabalení v bloku oboru názvů.  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>K vytvoření koncového bodu ASP.NET AJAX pro službu  
  
1.  Vytvoření konfigurace chování a zadejte [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování pro použití ASP.NET AJAX koncové body služby.  
  
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
  
2.  Vytvořit koncový bod pro službu, kterou používá <xref:System.ServiceModel.WebHttpBinding> a chování prvku ASP.NET AJAX, které jsou definované v předchozím kroku.  
  
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
  
1.  K hostování služby ve službě IIS, vytvořte nový soubor s názvem služby s příponou .svc v aplikaci. Tento soubor upravit přidáním odpovídající [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy informace pro službu. Například obsah v souboru služby pro `CalculatorService` ukázka obsahuje následující informace.  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  Další informace o hostování ve službě IIS najdete v tématu [postupy: hostování služby WCF ve službě IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Pro volání služby  
  
1.  Koncový bod je konfigurována na prázdnou adresu relativně k souboru .svc tak, aby služba je nyní k dispozici a může vyvolat odesílání požadavků na service.svc/\<operaci > – například service.svc/Add pro `Add` operaci. Můžete ji tak, že zadáte adresu URL koncového bodu do kolekce skripty ovládacího prvku ASP.NET AJAX skript správce. Příklad, naleznete v části [AJAX služby pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Postupy: Migrace webových služeb ASP.NET s podporou AJAX na WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
