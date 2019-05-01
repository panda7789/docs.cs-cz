---
title: 'Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 078580b96ab911f65790e58338951532cd7ad704
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047903"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zpřístupňuje koncový bod s podporou technologie ASP.NET AJAX, který může být volána z jazyka JavaScript na webové stránce klienta. Vytvořit takové koncový bod, můžete použít konfigurační soubor, stejně jako u všech ostatních koncových bodů WCF nebo používat metodu, která nevyžaduje žádné konfigurační prvky. Toto téma popisuje druhý přístup.  
  
 Vytvoření služby pomocí koncových bodů ASP.NET AJAX bez konfigurace, musí být služby hostovaný Internetové informační služby (IIS). Chcete-li aktivovat technologie ASP.NET AJAX koncový bod pomocí tohoto přístupu, zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jako parametr objekt pro vytváření v [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy v souboru SVC. Tento objekt pro vytváření vlastních je komponenta, která se automaticky nakonfiguruje koncového bodu ASP.NET AJAX tak, aby může být volána z jazyka JavaScript na webové stránce klienta.  
  
 Funkční příklad najdete v článku [služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Přehled konfigurace koncového bodu ASP.NET AJAX pomocí konfigurační prvky, naleznete v tématu [jak: Použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Chcete-li vytvořit základní služby WCF  
  
1. Definování základní kontraktu služby WCF s rozhraním označené <xref:System.ServiceModel.ServiceContractAttribute> atribut. Označit každou operaci s <xref:System.ServiceModel.OperationContractAttribute>. Nezapomeňte nastavit <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.  
  
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
  
2. Implementace `ICalculator` kontrakt služby s `CalculatorService`.  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. Definování oboru názvů pro `ICalculator` a `CalculatorService` implementace obalením v oboru bloku.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>K hostování služby v Internetové informační službě bez konfigurace  
  
1. Vytvořte nový soubor s názvem služby s příponou .svc v aplikaci. Tento soubor upravit tak, že přidáte odpovídající [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktiv informace pro službu. Určit, že <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se použije [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice pro automatickou konfiguraci koncového bodu ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. Sestavte službu a jeho volání z klienta. Internetové informační služby (IIS) se aktivuje při volání služby. Další informace o hostování ve službě IIS najdete v tématu [jak: Hostování služby WCF v IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Volání služby  
  
1. Koncový bod je nakonfigurována na prázdnou adresu relativní k souboru .svc tak, aby služba je nyní k dispozici a lze vyvolat pomocí zasílání požadavků na service.svc/\<operace > – například service.svc/Add pro `Add` operace. Můžete ho tak, že zadáte adresu URL služby do kolekce skriptů ovládací prvek správce skriptů ASP.NET AJAX. Příklad najdete v tématu [služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Příklad  
  
 Automaticky nakonfigurovat koncový bod se vytvoří prázdný adrese relativní k základní adrese URL. Konfigurační soubor lze také přidat a používat s tímto přístupem. Pokud konfigurační soubor obsahuje definic koncových bodů, tyto koncové body se přidají do koncového bodu automaticky nakonfigurované.  
  
 Například používá service.svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> a služba adresář obsahuje soubor Web.config, který definuje koncový bod pro stejnou službu pomocí <xref:System.ServiceModel.BasicHttpBinding> na relativní adrese "soap". V tomto případě služba obsahuje dva koncové body: jeden service.svc (která reaguje na požadavky technologie ASP.NET AJAX) a jiné na service.svc/soap (která reaguje na požadavky protokolu SOAP).  
  
 Pokud konfigurační soubor definuje koncový bod na prázdný relativní adrese a <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se používá, je vyvolána výjimka a službu nepodaří spustit.  
  
 Konfiguraci nelze použít ke změně nastavení pro koncový bod automaticky nakonfigurované. Pokud žádné nastavení (např. čtečka kvóty) musí být změněn, nesmí používat bez konfigurace přístup tak, že odeberete <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ze souboru .svc a vytvoření položky konfigurace pro koncový bod.  
  
 Pokud vaše služba vyžaduje režim kompatibility ASP.NET – například pokud se používá <xref:System.Web.HttpContext> třídy nebo mechanismy ověřování ASP.NET – konfigurační soubor je stále vyžadují k zapnutí nastavení v tomto režimu. Prvek konfigurace, vyžaduje se [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, který musí být přidán následujícím způsobem.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Další informace najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) tématu.  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Třída je odvozená třída <xref:System.ServiceModel.Activation.ServiceHostFactory>. Podrobné vysvětlení mechanizmus objekt pro vytváření hostitele služby, najdete v článku [rozšíření hostování pomocí ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) tématu.  
  
## <a name="see-also"></a>Viz také:

- [Vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Postupy: Migrace s povoleným AJAX webových služeb ASP.NET na WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
