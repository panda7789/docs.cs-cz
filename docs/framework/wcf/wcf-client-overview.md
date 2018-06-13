---
title: Klienti WCF – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: 03a9580bee6308ef53c7d2bc6e9dbe619c2048f7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808429"
---
# <a name="wcf-client-overview"></a>Klienti WCF – přehled
Tato část popisuje, co udělat klientských aplikací, jak nakonfigurovat, vytvoření a používání klienta Windows Communication Foundation (WCF) a jak zabezpečit klientské aplikace.  
  
## <a name="using-wcf-client-objects"></a>Pomocí objekty klienta WCF  
 Klientská aplikace je spravovaná aplikace, která používá klienta WCF ke komunikaci s jinou aplikací. Vytvoření klienta aplikace služby WCF vyžaduje následující kroky:  
  
1.  Získejte kontrakt služby, vazby a informace o adrese pro koncový bod služby.  
  
2.  Vytvoření klienta WCF pomocí těchto informací.  
  
3.  Volání operací.  
  
4.  Zavřete objekt klienta WCF.  
  
 Následující části popisují tyto kroky a zadejte stručné úvodní informace o následujících problémech:  
  
-   Zpracování chyb.  
  
-   Konfigurace a zabezpečení klientů.  
  
-   Vytváření objektů zpětného volání pro duplexní služby.  
  
-   Asynchronní volání služby.  
  
-   Volání metody službám pomocí klienta kanály.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Získat kontrakt služby, vazeb a adresy  
 Ve službě WCF služeb a klientů model kontrakty pomocí spravovaného atributy, rozhraní a metody. Pro připojení ke službě v aplikaci klienta, musíte získat informace o typu pro kontrakt služby. Obvykle to udělat pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), který stáhne metadata ze služby, převede na soubor spravované zdrojového kódu v jazyce, podle vašeho výběru a vytvoří klienta konfigurační soubor aplikace, můžete použít ke konfiguraci objektu klienta WCF. Například, pokud se chystáte vytvořit objekt klienta WCF pro vyvolání `MyCalculatorService`, a víte, že metadata pro tuto službu publikovaný v `http://computerName/MyCalculatorService/Service.svc?wsdl`, pak následující příklad kódu ukazuje, jak používat Svcutil.exe k získání `ClientCode.vb` souboru, který obsahuje kontrakt služby ve spravovaném kódu.  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Tento kód kontraktu můžete buď kompilovat do klientské aplikace nebo do jiné sestavení, klientská aplikace lze poté použít k vytvoření objektu klienta WCF. Konfigurační soubor můžete použít ke konfiguraci klientského objektu správně připojit ke službě.  
  
 Příklad tohoto procesu naleznete v části [postupy: vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Podrobnější informace o smlouvách najdete v tématu [kontrakty](../../../docs/framework/wcf/feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Vytvořit objekt klienta WCF  
 Klienta WCF je místní objekt, který reprezentuje služby WCF ve formuláři, který může klient použít ke komunikaci s vzdálené služby. Typy klienta WCF implementovat Cílová služba smlouvy, takže když vytvořit a nakonfigurovat jej, pak můžete objekt klient přímo k vyvolání operace služby. WCF běh převede volání metod zprávy, je odešle do služby, čeká na odpověď a vrátí tyto hodnoty k objektu klienta WCF jako návratové hodnoty nebo `out` nebo `ref` parametry.  
  
 Můžete taky objekty kanálu klienta WCF a připojit se pomocí služby. Podrobnosti najdete v tématu [Architektura klienta WCF](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Vytvoření nového objektu WCF  
 Pro ilustraci použití <xref:System.ServiceModel.ClientBase%601> třídy, předpokládá následující kontrakt jednoduché služby byla vygenerována z aplikace služby.  
  
> [!NOTE]
>  Pokud používáte Visual Studio k vytvoření vašeho klienta WCF, objekty jsou načteny automaticky do prohlížeče objektů při přidání odkazu na službu do projektu.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Pokud nepoužíváte Visual Studio, zkontrolujte kontrakt generovaný kód se najít typ, který rozšiřuje <xref:System.ServiceModel.ClientBase%601> a rozhraní kontraktu služby `ISampleService`. V takovém případě typu vypadá následující kód:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Tato třída můžete vytvořit jako objekt místní pomocí jednoho z konstruktorů, nakonfigurovat a pak použít pro připojení ke službě typu `ISampleService`.  
  
 Doporučujeme vytvořit objektu klienta WCF první a pak ho použít a zavřete uvnitř bloku try/catch – jeden. Neměli byste používat `using` – příkaz (`Using` v jazyce Visual Basic) vzhledem k tomu, že ho může maskování výjimky v určité režimy selhání. Další informace najdete v následujících částech a také [vyhnout problémům s příkazem Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Kontrakty, vazeb a adresy  
 Než bude možné vytvořit objekt klienta WCF, je nutné nakonfigurovat klientského objektu. Konkrétně musí mít služby *koncový bod* používat. Koncový bod je kombinace kontraktu služby, vazbu a adresu. (Další informace o koncových bodech najdete v tématu [koncové body: adresy, vazby a kontrakty](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md).) Tyto informace se obvykle nachází ve [ \<endpoint >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) element v souboru konfigurace aplikace klienta, jako je třeba nástroje Svcutil.exe generuje a že je načtený automaticky při vytváření vašeho klienta objekt. Oba typy klienta WCF také mají přetížení, které vám umožní prostřednictvím kódu programu zadejte tyto informace.  
  
 Například vygenerovaný konfigurační soubor pro `ISampleService` použít v předchozím příklady obsahuje následující informace o koncový bod.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Tento konfigurační soubor Určuje koncový bod cíl v `<client>` elementu. Další informace o používání více cílové koncové body, najdete v článku <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> konstruktory.  
  
## <a name="calling-operations"></a>Volání operace  
 Jednou máte klienta objekt vytvořený a nakonfigurovaný, vytvořit blok try/catch –, volání operací stejným způsobem, který jste kdyby byly místní objekt a zavřete objekt klienta WCF. Když klientské aplikace volá operaci první, WCF automaticky otevře základní kanál a základní kanál je uzavřen, pokud je objekt recykluje. (Alternativně můžete také explicitně otevřete a zavřete kanál před nebo po volání jiné operace.)  
  
 Například pokud máte následující kontrakt služby:  
  
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
  
 Vytvořením objektu klienta WCF můžete volat operace a volání její metody jako následující příklad kódu ukazuje. Všimněte si, že v rámci bloku try/catch – jeden k otevírání, volání a zavření objektu klienta WCF. Další informace najdete v tématu [přístup k službám pomocí klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) a [vyhnout problémům s příkazem Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Zpracování chyb  
 Výjimky může dojít v aplikaci klienta, když otevírání základní klienta kanálu (jestli explicitně nebo automaticky voláním operace), pomocí objektu klienta nebo kanál volat operace, nebo při zavření základní kanálem klienta. Se minimálně doporučuje, aby aplikace očekávají, že pro zpracování možné <xref:System.TimeoutException?displayProperty=nameWithType> a <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> výjimky kromě žádné <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objekty vyvolána výjimka v důsledku chyb SOAP vrácených operací. Pro klientské aplikace, jako jsou vyvolány SOAP chyb uvedených ve smlouvě operace <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> kde parametr typu je typ podrobnosti o chybě protokolu SOAP. Další informace o zpracování chybové stavy v aplikaci klienta najdete v tématu [odesílání a přijímání chyb](../../../docs/framework/wcf/sending-and-receiving-faults.md). Úplná ukázka služby zobrazí způsob zpracování chyb v klientovi, najdete v části [očekává výjimky](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Konfigurace a zabezpečení klientů  
 Konfigurace klienta začíná načítání požadované informace o cílové koncový bod pro klienta nebo kanál objektu, která obvykle z konfiguračního souboru, i když můžete také načíst tyto informace programově pomocí konstruktorů klienta a vlastnosti. Však jsou zapotřebí další konfigurační kroky, chcete-li povolit určité chování klienta a pro mnoho scénářů zabezpečení.  
  
 Například požadavky na zabezpečení pro kontraktů služby jsou deklarované v rozhraní kontraktu služby, a pokud Svcutil.exe vytvořit konfigurační soubor, že soubor obvykle obsahuje vazbu, který podporuje požadavky na zabezpečení služby. V některých případech ale další konfigurace zabezpečení může být vyžadovat, například konfigurace pověření klienta. Úplné informace o konfiguraci zabezpečení pro klienty WCF najdete v tématu [zabezpečení klientů](../../../docs/framework/wcf/securing-clients.md).  
  
 Kromě toho lze v klientských aplikacích, jako je například vlastní chování běhové povolit vlastní úpravy. Další informace o tom, jak nakonfigurovat chování vlastní klienta najdete v tématu [konfigurace chování klientů](../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Vytváření objektů zpětného volání pro duplexní služby  
 Duplexní služby zadejte kontraktu zpětného volání, které klientská aplikace musí implementovat, aby bylo možné poskytnout objekt zpětného volání pro službu, kterou chcete volat podle požadavků kontrakt. I když zpětného volání objekty nejsou úplné služby (například nelze inicializovat, kanál s objektem zpětného volání), za účelem implementace a konfigurace se může považovat za typ služby.  
  
 Musí být klienti duplexní služby:  
  
-   Implementace třídy kontrakt zpětného volání.  
  
-   Vytvoření instance třídy implementace kontraktu zpětného volání a použít ho k vytvoření <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> objekt předaný do konstruktoru klienta WCF.  
  
-   Vyvolání operací a zpracovat zpětná volání operace.  
  
 Duplexní WCF klienta objekty fungují jako jejich podavače protějšky, s tím rozdílem, že jejich zpřístupnění potřebných k podpoře zpětná volání, včetně konfiguraci této služby zpětného volání funkce.  
  
 Například můžete ovládat různé aspekty zpětného volání objektu modul runtime chování pomocí vlastnosti <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> atribut k třídě zpětného volání. Dalším příkladem je použití <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> třída povolit vrácení informací o výjimce do služby, které volají objekt zpětného volání. Další informace najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md). Kompletní příklad, najdete v části [duplexní](../../../docs/framework/wcf/samples/duplex.md).  
  
 V počítačích se systémem Windows XP systémem Internetové informační služby (IIS) 5.1, duplexní klienti musí zadat základní adresu klienta pomocí <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> je vyvolána třída nebo výjimku. Následující příklad kódu ukazuje, jak to udělat v kódu.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Následující kód ukazuje, jak to udělat v konfiguračním souboru  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Asynchronní volání služby  
 Jak se nazývají operace, záleží zcela vývojáře klienta. Je to proto, že zprávy, které tvoří operace lze mapovat na synchronní nebo asynchronní metody vyjádřené ve spravovaném kódu. Proto, pokud chcete vytvořit klienta, který volá asynchronní operace, můžete použít Svcutil.exe Generovat asynchronní klienta kódu pomocí `/async` možnost. Další informace najdete v tématu [postupy: asynchronní volání operací služby](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Volání služby prostřednictvím kanálů klienta WCF  
 Rozšíření typů klientů WCF <xref:System.ServiceModel.ClientBase%601>, které je odvozena z <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> rozhraní vystavit podkladový systém kanálu. Můžete vyvolat služby pomocí cíl kontrakt služby s <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> třídy. Podrobnosti najdete v tématu [Architektura klienta WCF](../../../docs/framework/wcf/feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
