---
title: Klienti WCF – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: 34abe6b07cebc446324785bde1061c7aa2b04e4a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115918"
---
# <a name="wcf-client-overview"></a>Klienti WCF – přehled
Tato část popisuje, co dělat klientské aplikace, jak konfigurovat, vytvořit a používat klienta Windows Communication Foundation (WCF) a tom, jak zabezpečit klientské aplikace.  
  
## <a name="using-wcf-client-objects"></a>Použití objektů klienta WCF  
 Klientská aplikace je spravovaná aplikace, která používá klienta WCF pro komunikaci s jinou aplikací. K vytvoření klienta aplikace služby WCF vyžaduje následující kroky:  
  
1.  Získáte smlouvu, vazby a informace o adrese koncového bodu služby.  
  
2.  Vytvořte klienta WCF pomocí těchto informací.  
  
3.  Volání operací.  
  
4.  Zavřete objekt klienta WCF.  
  
 Následující oddíly popisují tyto kroky a poskytují stručné úvodní informace k následujícím problémům:  
  
-   Zpracování chyb.  
  
-   Konfigurace a zabezpečení klientů.  
  
-   Vytváření objektů zpětného volání pro duplexní služby.  
  
-   Asynchronní volání služby.  
  
-   Volání služby pomocí kanály klientů.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Získat smlouvu, vazeb a adresy  
 Ve službě WCF služeb a klientů modelu kontrakty pomocí spravované atributy, rozhraní a metody. Připojení ke službě v klientské aplikaci, potřebujete získat informace o typu pro kontrakt služby. Obvykle to provést pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), která stahuje metadata ze služby, převede ho na soubor spravovaném zdrojovém kódu v jazyce podle vašeho výběru a vytvoří klienta konfigurační soubor aplikace, které můžete použít ke konfiguraci objektu klienta WCF. Například, pokud se chystáte vytvořit objekt klienta WCF pro vyvolání `MyCalculatorService`, a víte, že metadata pro danou službu je zveřejněný na webu `http://computerName/MyCalculatorService/Service.svc?wsdl`, pak následující příklad kódu ukazuje způsob použití Svcutil.exe k získání `ClientCode.vb` souboru, který obsahuje kontraktu služby ve spravovaném kódu.  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Můžete buď kompilaci tohoto kontraktu kódu do klientské aplikace nebo na jiná sestavení, která klientská aplikace můžete potom použít k vytvoření objektu klienta WCF. Konfigurační soubor můžete použít ke konfiguraci objektu klienta správně připojit ke službě.  
  
 Příklad tohoto procesu najdete v tématu [jak: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Podrobnější informace o smlouvách, naleznete v tématu [kontrakty](../../../docs/framework/wcf/feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Vytvoření objektu klienta WCF  
 Klienta WCF se místní objekt, který představuje služby WCF ve formuláři, který může klient použít ke komunikaci se vzdálenou službou. Typ klienta WCF implementovat cílovou službu smlouvy, takže když vytvořit a nakonfigurovat ho, pak můžete použít objekt klienta přímo k vyvolání operace služby. WCF běhu převede volání metod na zprávy, odešle do služby, čeká na odpověď a vrátí tyto hodnoty do objektu klienta WCF jako návratové hodnoty nebo `out` nebo `ref` parametry.  
  
 Objekty kanálu klienta WCF můžete také použít k připojení a použití služby. Podrobnosti najdete v tématu [Architektura klienta WCF](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Vytvoření nového objektu WCF  
 Pro ilustraci použití <xref:System.ServiceModel.ClientBase%601> třídy, se předpokládá následující jednoduchý smlouvu vygenerování aplikace služby.  
  
> [!NOTE]
>  Pokud používáte Visual Studio k vytvoření klienta WCF, objekty jsou načteny automaticky do prohlížeče objektů při přidání odkazu na službu do projektu.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Pokud nepoužíváte Visual Studio, zkontrolujte kódu generovaného kontraktu se najít typ, který rozšiřuje <xref:System.ServiceModel.ClientBase%601> a rozhraní servisní smlouvy `ISampleService`. Tento typ v tomto případě bude vypadat jako v následujícím kódu:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Tuto třídu lze vytvořit jako objekt místní pomocí jednoho z konstruktorů, konfiguraci a pak použije k připojení ke službě typu `ISampleService`.  
  
 Doporučuje se, že nejprve vytvořit objekt klienta WCF a potom ho použít a zavřít uvnitř bloku try/catch – jeden. Neměli byste používat `using` – příkaz (`Using` v jazyce Visual Basic) vzhledem k tomu, že to může maskovat výjimky v určitých režimů selhání. Další informace najdete v částech stejně jako [použití zavřít a Abort k uvolnění prostředků klienta WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Kontrakty, vazeb a adresy  
 Před vytvořením objektu klienta WCF, je nutné nakonfigurovat objekt klienta. Konkrétně musí nabízet službu *koncový bod* používat. Koncový bod je kombinace kontraktu služby, vazbu a adresu. (Další informace o koncových bodech najdete v tématu [koncové body: Adresy, vazby a kontrakty](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md).) Tyto informace je obvykle umístěná v [ \<koncový bod >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) elementu v souboru konfigurace aplikace klienta, jako je ta nástroje Svcutil.exe generuje a načte se automaticky při vytváření vašeho klienta objekt. Oba typy klienta WCF také mají přetížení, které vám umožní prostřednictvím kódu programu zadejte tyto informace.  
  
 Například generované konfiguračního souboru pro `ISampleService` použité v předchozím příklady obsahuje následující informace koncového bodu.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Tento konfigurační soubor Určuje cílový koncový bod v `<client>` elementu. Další informace o používání více cílové koncové body, najdete v článku <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> konstruktory.  
  
## <a name="calling-operations"></a>Volání operace  
 Jakmile mít klienta objekt vytvořený a nakonfigurovaný, vytvoření bloku try/catch, volání operací v stejně, jako by šlo místní objekt a zavření objektu klienta WCF. Když klientská aplikace volá první operace, WCF se automaticky otevře základním kanálu a základním kanálu je uzavřen, když objekt recykluje. (Alternativně můžete také explicitně otevřít a zavřete kanál před nebo po volání dalších operací.)  
  
 Pokud například máte následující kontraktu služby:  
  
```csharp  
namespace Microsoft.ServiceModel.Samples  
{  
    using System;  
    using System.ServiceModel;  
  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
   {  
        [OperationContract]  
        double Add(double n1, double n2);  
        [OperationContract]  
        double Subtract(double n1, double n2);  
        [OperationContract]  
        double Multiply(double n1, double n2);  
        [OperationContract]  
        double Divide(double n1, double n2);  
    }  
}  
```  
  
```vb  
Namespace Microsoft.ServiceModel.Samples  
  
    Imports System  
    Imports System.ServiceModel  
  
    <ServiceContract(Namespace:= _  
    "http://Microsoft.ServiceModel.Samples")> _   
   Public Interface ICalculator  
        <OperationContract> _   
        Function Add(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Subtract(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Multiply(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
     Function Divide(n1 As Double, n2 As Double) As Double  
End Interface  
```  
  
 Můžete volat operace tak, že vytvoříte objekt klienta WCF a volat jeho metody jako následující příklad kódu ukazuje. Všimněte si, že dochází v rámci bloku try/catch – jeden zahájení, volání funkce a zavření objektu klienta WCF. Další informace najdete v tématu [přístup ke službám pomocí klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) a [použití zavřít a Abort k uvolnění prostředků klienta WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Zpracování chyb  
 Může dojít k výjimkám v klientské aplikaci otevřete příslušný klient kanálu (ať už výslovně nebo automaticky pomocí volání operace), pomocí objektu klienta nebo kanál k volání operací, nebo při zavření základním kanálu klienta. Doporučujeme přinejmenším, že aplikace očekávají, že pro zpracování možné <xref:System.TimeoutException?displayProperty=nameWithType> a <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> výjimky spolu s některou <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objekty vyvolána v důsledku chyb SOAP vrácena operacemi. Pro klientské aplikace, jako jsou vyvolány chyb SOAP, které jsou uvedené ve smlouvě operace <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> kde parametr typu je typ podrobností chybu protokolu SOAP. Další informace o zpracování chybové stavy v klientské aplikaci najdete v tématu [odesílání a příjem chyb](../../../docs/framework/wcf/sending-and-receiving-faults.md). Úplná ukázka zobrazí zpracování chyb v klientovi, najdete v části [očekávané výjimky](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Konfigurace a zabezpečení klientů  
 Konfigurace klienta začíná načítání požadované informace o koncovém bodu cílového objektu klienta nebo kanálu, obvykle z konfiguračního souboru, i když můžete také načíst těchto informací prostřednictvím kódu programu pomocí klienta konstruktory a vlastnosti. Však je potřeba provést další konfigurační kroky povolit určité chování klienta a pro řadu scénářů zabezpečení.  
  
 Například požadavky na zabezpečení pro servisní smlouvy, které jsou deklarované v rozhraní servisní smlouvy, a pokud Svcutil.exe vytvořit konfigurační soubor, tento soubor obvykle obsahuje vazbu, která je schopný zajistit podporu požadavky na zabezpečení služby. V některých případech však další konfigurace zabezpečení může vyžadovat, například ke konfiguraci přihlašovacích údajů klienta. Podrobnější informace o konfiguraci zabezpečení pro klienty WCF najdete v článku [zabezpečení klientů](../../../docs/framework/wcf/securing-clients.md).  
  
 Kromě toho některé vlastní úpravy se dá nastavit v klientských aplikacích, jako jsou vlastní chování za běhu. Další informace o tom, jak nakonfigurovat vlastní chování najdete v tématu [konfigurace chování klientů](../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Vytváření objektů zpětného volání pro duplexní služby  
 Duplexní služby určete kontrakt zpětného volání, které klientská aplikace musí implementovat, aby bylo možné poskytnout objekt zpětného volání pro službu pro volání podle požadavků smlouvy. I když objekty zpětného volání nejsou úplné služby (například nelze spustíte kanál s objekt zpětného volání), za účelem implementace a konfigurace, můžete představit jako typ služby.  
  
 Klienti duplexní služby musí:  
  
-   Implementace třídy kontrakt zpětného volání.  
  
-   Vytvoření instance třídy implementace kontraktu zpětného volání a použijte ji k vytvoření <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> objekt předaný konstruktoru klienta WCF.  
  
-   Vyvolání operací a zpracování zpětných volání operace.  
  
 Duplexní WCF klienta objektů funkce stejně jako jejich protějšky podavače, s tím rozdílem, že zveřejňovaly potřebných k podpoře zpětná volání, včetně konfigurace služby zpětného volání funkce.  
  
 Například můžete ovládat různé aspekty chování za běhu objekt zpětného volání pomocí vlastnosti <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> atribut ve třídě zpětného volání. Dalším příkladem je použití <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> třídy umožňující vrátit informace o výjimce ke službám, které volají objekt zpětného volání. Další informace najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md). Úplnou ukázku najdete v tématu [duplexní](../../../docs/framework/wcf/samples/duplex.md).  
  
 V počítačích se systémem Windows XP systémem Internetové informační služby (IIS) 5.1, duplexní budou muset klienti zadat pomocí základní adresa klienta <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> třídy nebo výjimka je vyvolána výjimka. Následující příklad kódu ukazuje, jak to provést v kódu.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Následující kód ukazuje, jak to provést v konfiguračním souboru  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Asynchronní volání služeb  
 Jak operace jsou označovány jako je zcela v kompetenci vývojáře klienta. Je to proto, že zprávy, které tvoří operace lze mapovat na synchronní nebo asynchronní metody vyjádřené ve spravovaném kódu. Proto pokud chcete sestavit klienta, který asynchronně volá operace, můžete použít Svcutil.exe ke generování kódu pomocí asynchronního klientského `/async` možnost. Další informace najdete v tématu [jak: Asynchronní volání operací služby](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Volání služby pomocí kanálů klienta WCF  
 Typy klienta WCF rozšířit <xref:System.ServiceModel.ClientBase%601>, který je odvozen od <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> rozhraní ke zveřejnění základní kanál systému. Služby lze vyvolat pomocí cílové kontrakt služby s <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> třídy. Podrobnosti najdete v tématu [Architektura klienta WCF](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
