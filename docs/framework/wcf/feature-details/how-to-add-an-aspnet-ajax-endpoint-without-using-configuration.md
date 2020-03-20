---
title: 'Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9935e2a7738796fff9a037b09237a6acbf7bf988
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185133"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru
Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje koncový bod s podporou ASP.NET AJAX, který lze volat z Jazyka JavaScript na klientském webu. Chcete-li vytvořit takový koncový bod, můžete buď použít konfigurační soubor, stejně jako u všech ostatních koncových bodů WCF, nebo použít metodu, která nevyžaduje žádné konfigurační prvky. Toto téma ukazuje druhý přístup.  
  
 Chcete-li vytvořit služby s ASP.NET koncovými body AJAX bez konfigurace, musí být služby hostovány internetovou informační službou (IIS). Chcete-li aktivovat koncový bod ASP.NET <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> AJAX pomocí tohoto přístupu, zadejte parametr Factory ve směrnici [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) v souboru .svc. Tato vlastní továrna je komponenta, která automaticky konfiguruje koncový bod ASP.NET AJAX tak, aby jej bylo možné volat z JavaScriptu na klientském webu.  
  
 Pracovní příklad naleznete v tématu [služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Přehled konfigurace koncového bodu ASP.NET AJAX pomocí konfiguračních prvků naleznete v tématu [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Vytvoření základní služby WCF  
  
1. Definujte základní servisní smlouvu WCF <xref:System.ServiceModel.ServiceContractAttribute> s rozhraním označeným atributem. Každou operaci označte pomocí <xref:System.ServiceModel.OperationContractAttribute>. Nezapomeňte nastavit <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.  
  
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
  
2. Dokončujte `ICalculator` `CalculatorService`servisní smlouvu s .  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. Definujte obor názvů `ICalculator` `CalculatorService` pro a implementace zabalením do bloku oboru názvů.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Hostování služby v Internetové informační službě bez konfigurace  
  
1. Vytvořte nový soubor s názvem služby s příponou SVC v aplikaci. Upravte tento soubor [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) přidáním příslušných informací směrnice ServiceHost pro službu. Určete, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> že má být použit v [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice automaticky konfigurovat koncový bod ASP.NET AJAX.  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. Sestavení služby a volání z klienta. Internetová informační služba (IIS) aktivuje službu při volání. Další informace o hostování ve službě IIS naleznete v [tématu How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Chcete-li volat službu  
  
1. Koncový bod je konfigurován na prázdnou adresu vzhledem k souboru .svc, takže služba je nyní k dispozici\<a může být vyvolána odesláním požadavků `Add` na service.svc/ operace> - například service.svc/Add pro operaci. Můžete jej použít zadáním adresy URL služby do kolekce Skripty ovládacího prvku ASP.NET AJAX Script Manager. Příklad naleznete v tématu [služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Příklad  
  
 Automaticky nakonfigurovaný koncový bod je vytvořen na prázdné adrese vzhledem k základní adrese URL. Konfigurační soubor lze také přidat a použít s tímto přístupem. Pokud konfigurační soubor obsahuje definice koncových bodů, budou tyto koncové body přidány do automaticky nakonfigurovaného koncového bodu.  
  
 Například service.svc používá <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> a adresář služby obsahuje soubor Web.config, který definuje koncový <xref:System.ServiceModel.BasicHttpBinding> bod pro stejnou službu pomocí relativní adresy "soap". V tomto případě služba obsahuje dva koncové body: jeden na service.svc (který reaguje na ASP.NET požadavky AJAX) a další na service.svc/soap (který reaguje na požadavky SOAP).  
  
 Pokud konfigurační soubor definuje koncový bod na <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> prázdnou relativní adresu a používá se, je vyvolána výjimka a služba se nespustí.  
  
 Konfiguraci nelze použít k úpravě nastavení automaticky konfigurovaného koncového bodu. Pokud je nutné změnit jakékoli nastavení (například kvótu čtečky), nesmíte použít <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> přístup bez konfigurace odebráním souboru SVC a vytvořením položky konfigurace pro koncový bod.  
  
 Pokud vaše služba vyžaduje ASP.NET režimu kompatibility <xref:System.Web.HttpContext> – například pokud používá mechanismy autorizace třídy nebo ASP.NET – konfigurační soubor je stále nutné zapnout tento režim. Požadovaný konfigurační prvek je [ \<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) prvek, který musí být přidán následujícím způsobem.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Další informace naleznete v tématu [WCF Services a ASP.NET.](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
  
 Třída <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> je odvozené třídy <xref:System.ServiceModel.Activation.ServiceHostFactory>. Podrobné vysvětlení mechanismu továrny hostitele služby naleznete v tématu [Rozšíření hostingu pomocí ServiceHostFactory.](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
  
## <a name="see-also"></a>Viz také

- [Vytváření služeb WCF pro ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
