---
title: "Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b90ecd94f439472c89d0c075c8b7486abeacf38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Umožňuje vytvořit službu, která zveřejňuje koncový bod podporou technologie ASP.NET AJAX, který lze volat z jazyka JavaScript na webovém serveru klienta. Pokud chcete vytvořit takové koncový bod, můžete pomocí konfiguračního souboru, stejně jako u všech dalších koncových bodů WCF nebo použít metodu, která nevyžaduje, aby všechny konfigurace – elementy. Toto téma popisuje druhý přístup.  
  
 Vytvoření služby pomocí koncových bodů prvku ASP.NET AJAX bez konfigurace, musí být služby hostované Internetové informační služby (IIS). Pokud chcete aktivovat tento přístup pomocí prvku ASP.NET AJAX koncový bod, zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jako parametr objekt pro vytváření v [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy v souboru .svc. Tento vlastní objekt pro vytváření je součást, který automaticky nakonfiguruje koncového bodu ASP.NET AJAX tak, aby může být volána z jazyka JavaScript na webovém serveru klienta.  
  
 Příklad pracovní najdete v tématu [služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Přehled konfigurace koncového bodu ASP.NET AJAX pomocí konfigurace – elementy, najdete v části [postupy: použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Chcete-li vytvořit základní služby WCF  
  
1.  Zadejte základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt služby s rozhraním označené jako <xref:System.ServiceModel.ServiceContractAttribute> atribut. Označit každou operaci s <xref:System.ServiceModel.OperationContractAttribute>. Nastavte <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.  
  
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
  
2.  Implementace `ICalculator` kontrakt služby s `CalculatorService`.  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  Zadejte obor názvů pro `ICalculator` a `CalculatorService` implementace podle jejich zabalení v bloku oboru názvů.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>K hostování služby v Internetové informační službě bez konfigurace  
  
1.  Vytvořte nový soubor s názvem služby s příponou .svc v aplikaci. Tento soubor upravit přidáním odpovídající [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy informace pro službu. Určit, že <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> má být použita v [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice pro automatickou konfiguraci koncového bodu ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  Sestavte službu a volání z klienta. Internetové informační služby (IIS) aktivuje službu při volání. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]hostování ve službě IIS, najdete v části [postupy: hostování služby WCF ve službě IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Pro volání služby  
  
1.  Koncový bod je konfigurována na prázdnou adresu relativně k souboru .svc tak, aby služba je nyní k dispozici a může vyvolat odesílání požadavků na service.svc/\<operaci > – například service.svc/Add pro `Add` operaci. Můžete ji tak, že zadáte adresu URL služby do kolekce skripty ovládacího prvku ASP.NET AJAX skript správce. Příklad, naleznete v části [služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Příklad  
  
 Koncový bod automaticky nakonfiguruje se vytvoří na prázdnou adresu relativně k základní adresu URL. Konfigurační soubor můžete taky přidat a používat s tímto přístupem. Pokud konfigurační soubor obsahuje definice koncových bodů, tyto koncové body se přidají do koncového bodu automaticky nakonfigurované.  
  
 Například používá service.svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> a adresář služby obsahuje soubor Web.config, který definuje koncový bod pro stejné služby pomocí <xref:System.ServiceModel.BasicHttpBinding> na adrese relativní "soap". V takovém případě služba obsahuje dva koncové body: jeden po service.svc (který reaguje na požadavky ASP.NET AJAX) a jiné na service.svc/soap (který reaguje na požadavky protokolu SOAP).  
  
 Pokud konfigurační soubor definuje koncový bod na prázdnou adresu relativní a <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se používá, je vyvolána výjimka, a službu nepodaří spustit.  
  
 Konfigurace nelze použít k úpravě nastavení pro koncový bod automaticky nakonfigurované. Pokud žádné nastavení (například čtečky kvótu) musí být změněna, nesmí používat přístup bez konfigurace odebráním <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ze souboru .svc a vytvořením položky konfigurace pro koncový bod.  
  
 Pokud vaše služba vyžaduje režim kompatibility ASP.NET – například pokud se používá <xref:System.Web.HttpContext> třídu nebo mechanismy ověřování ASP.NET – konfigurační soubor je stále vyžadují k zapnutí v tomto režimu. Konfigurační element požadované je [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, který musí být přidán následujícím způsobem.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) tématu.  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Třída je třídu odvozenou z <xref:System.ServiceModel.Activation.ServiceHostFactory>. Podrobné vysvětlení mechanismus objekt pro vytváření hostitele služby, najdete v článku [rozšíření hostování pomocí třídy ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) tématu.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Postupy: Migrace webových služeb ASP.NET s podporou AJAX na WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
