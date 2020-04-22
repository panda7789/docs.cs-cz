---
title: Klienti WCF – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: b314b61584e45ac5e80a248e639bdac427ba4a57
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "82021721"
---
# <a name="wcf-client-overview"></a>Přehled klienta WCF

Tato část popisuje, co klientské aplikace dělají, jak konfigurovat, vytvářet a používat klienta WCF (Windows Communication Foundation) a jak zabezpečit klientské aplikace.  
  
## <a name="using-wcf-client-objects"></a>Použití objektů klienta WCF  
 Klientská aplikace je spravovaná aplikace, která ke komunikaci s jinou aplikací používá klienta WCF. Vytvoření klientské aplikace pro službu WCF vyžaduje následující kroky:  
  
1. Získejte servisní smlouvu, vazby a informace o adrese pro koncový bod služby.  
  
2. Vytvořte klienta WCF pomocí této informace.  
  
3. Volejte operace.  
  
4. Zavřete objekt klienta WCF.  
  
Následující části popisují tyto kroky a poskytují stručný úvod k následujícím otázkám:  
  
- Zpracování chyb.  
  
- Konfigurace a zabezpečení klientů.  
  
- Vytváření objektů zpětného volání pro duplexní služby.  
  
- Volání služeb asynchronně.  
  
- Volání služeb pomocí klientských kanálů.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Získání servisní smlouvy, vazeb a adres  
 V WCF služby a klienti model smlouvy pomocí spravované atributy, rozhraní a metody. Chcete-li se připojit ke službě v klientské aplikaci, musíte získat informace o typu pro servisní smlouvu. Obvykle získáte informace o typu pro servisní smlouvy pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md). Nástroj stáhne metadata ze služby, převede je na soubor spravovaného zdrojového kódu v jazyce podle vašeho výběru a vytvoří konfigurační soubor klientské aplikace, který můžete použít ke konfiguraci objektu klienta WCF. Například pokud se chystáte vytvořit objekt klienta `MyCalculatorService`WCF vyvolat , a víte, že metadata pro tuto službu je publikován na `http://computerName/MyCalculatorService/Service.svc?wsdl`, pak následující `ClientCode.vb` příklad kódu ukazuje, jak použít Svcutil.exe získat soubor, který obsahuje servisní smlouvy ve spravovaném kódu.  
  
```console  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Tento kód smlouvy můžete zkompilovat do klientské aplikace nebo do jiného sestavení, které pak může klientská aplikace použít k vytvoření objektu klienta WCF. Konfigurační soubor můžete použít ke konfiguraci objektu klienta pro správné připojení ke službě .  
  
 Příklad tohoto procesu naleznete v [tématu How to: Create a Client](how-to-create-a-wcf-client.md). Podrobnější informace o smlouvách naleznete v [tématu Contracts](./feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Vytvoření objektu klienta WCF  
 WCF klient je místní objekt, který představuje službu WCF ve formuláři, který klient může použít ke komunikaci se vzdálenou službou. WCF typy klientů implementovat kontrakt cílové služby, takže při vytvoření a nakonfigurovat, pak můžete použít objekt klienta přímo vyvolat operace služby. WCF doba běhu převede volání metody do zprávy, odešle je do služby, naslouchá odpovědi a vrátí tyto `out` `ref` hodnoty wcf klienta objektu jako vrácené hodnoty nebo parametry.  
  
 Můžete také použít WCF objekty kanálu klienta pro připojení a použití služeb. Podrobnosti naleznete v [tématu WCF Client Architecture](./feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Vytvoření nového objektu WCF  
 Pro ilustraci <xref:System.ServiceModel.ClientBase%601> použití třídy předpokládejme, že z aplikace služby byla vygenerována následující jednoduchá servisní smlouva.  
  
> [!NOTE]
> Pokud používáte Visual Studio k vytvoření wcf klienta, objekty se načtou automaticky do prohlížeče objektů při přidání odkazu na službu do projektu.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Pokud nepoužíváte Visual Studio, zkontrolujte kód generované smlouvy najít <xref:System.ServiceModel.ClientBase%601> typ, který `ISampleService`rozšiřuje a rozhraní servisní smlouvy . V tomto případě tento typ vypadá jako následující kód:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Tuto třídu lze vytvořit jako místní objekt pomocí jednoho z konstruktorů, nakonfigurován a `ISampleService`poté použít pro připojení ke službě typu .  
  
 Doporučujeme nejprve vytvořit objekt klienta WCF a potom jej použít a zavřít uvnitř jednoho bloku try/catch. Nepoužívejte `using` příkaz (v`Using` jazyce Visual Basic), protože může maskovat výjimky v určitých režimech selhání. Další informace naleznete v následujících částech a [také použití zavřít a přerušit uvolnění prostředků klienta WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Smlouvy, vazby a adresy  
 Před vytvořením objektu klienta WCF je nutné nakonfigurovat objekt klienta. Konkrétně musí mít *koncový bod* služby k použití. Koncový bod je kombinace smlouvy o poskytování služeb, vazby a adresy. (Další informace o koncových bodech naleznete [v tématu Koncové body: Adresy, vazby a smlouvy](./feature-details/endpoints-addresses-bindings-and-contracts.md).) Tyto informace jsou obvykle umístěny v [ \<koncovém bodě>](../configure-apps/file-schema/wcf/endpoint-of-client.md) prvek v konfiguračním souboru klientské aplikace, jako je například ten, který generuje nástroj Svcutil.exe, a je načten automaticky při vytváření objektu klienta. Oba typy klientů WCF mají také přetížení, které umožňují programově zadat tyto informace.  
  
 Například generovaný konfigurační soubor pro `ISampleService` použitý v předchozích příkladech obsahuje následující informace o koncovém bodu.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Tento konfigurační soubor určuje `<client>` cílový koncový bod v elementu. Další informace o použití více cílových <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> koncových bodů naleznete v tématu <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> nebo konstruktory.  
  
## <a name="calling-operations"></a>Volání operací  
 Jakmile máte objekt klienta vytvořené a nakonfigurované, vytvořte try/catch bloku, volání operací stejným způsobem, jako byste měli v případě, že objekt byl místní a zavřete objekt klienta WCF. Když klientská aplikace volá první operaci, WCF automaticky otevře základní kanál a základní kanál je uzavřen při recyklaci objektu. (Případně můžete také explicitně otevřít a zavřít kanál před nebo po volání jiných operací.)  
  
 Máte-li například následující servisní smlouvu:  
  
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
  
 Operace můžete volat vytvořením objektu klienta WCF a voláním jeho metod, jak ukazuje následující příklad kódu. Otevření, volání a zavření objektu klienta WCF dochází v rámci jednoho try/catch bloku. Další informace naleznete [v tématu Přístup ke službám pomocí klienta WCF](./feature-details/accessing-services-using-a-client.md) a [použití zavřít a přerušit uvolnění prostředků klienta WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Zpracování chyb  
 Výjimky může dojít v klientské aplikaci při otevírání základního kanálu klienta (ať už explicitně nebo automaticky voláním operace), pomocí klienta nebo objektu kanálu volat operace nebo při zavírání základního kanálu klienta. Doporučuje se minimálně, že aplikace <xref:System.TimeoutException?displayProperty=nameWithType> očekávají <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> zpracování možné a <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> výjimky kromě všechny objekty vyvolány v důsledku chyb SOAP vrácených operacemi. Chyby SOAP zadané ve smlouvě operace jsou <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> vyvolány do klientských aplikací jako kde parametr typu je typ podrobností chyby SOAP. Další informace o zpracování chybových stavů v klientské aplikaci naleznete v [tématu Sending and Receiving Faults](sending-and-receiving-faults.md). Kompletní ukázka ukazuje, jak zpracovat chyby v klientovi, naleznete v tématu [očekávané výjimky](./samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Konfigurace a zabezpečení klientů  
 Konfigurace klienta začíná požadovaným načítáním informací cílového koncového bodu pro objekt klienta nebo kanálu, obvykle z konfiguračního souboru, i když můžete také načíst tyto informace programově pomocí konstruktorů klienta a vlastností. Další kroky konfigurace jsou však nutné povolit určité chování klienta a pro mnoho scénářů zabezpečení.  
  
 Například požadavky na zabezpečení pro servisní smlouvy jsou deklarovány v rozhraní servisní smlouvy a pokud Svcutil.exe vytvořil konfigurační soubor, tento soubor obvykle obsahuje vazbu, která je schopna podporovat požadavky na zabezpečení služby. V některých případech však může být vyžadována další konfigurace zabezpečení, například konfigurace pověření klienta. Úplné informace o konfiguraci zabezpečení pro klienty WCF naleznete v tématu [Zabezpečení klientů](securing-clients.md).  
  
 Kromě toho některé vlastní změny mohou být povoleny v klientských aplikacích, jako je například vlastní chování za běhu. Další informace o konfiguraci chování vlastního klienta naleznete v [tématu Konfigurace chování klienta](configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Vytváření objektů zpětného volání pro duplexní služby  
 Duplexní služby zadat kontrakt zpětného volání, který musí klientská aplikace implementovat, aby poskytla objekt zpětného volání pro službu volat podle požadavků smlouvy. Přestože objekty zpětného volání nejsou úplné služby (například nelze zahájit kanál s objektem zpětného volání), pro účely implementace a konfigurace je lze považovat za druh služby.  
  
 Klienti duplexních služeb musí:  
  
- Implementujte třídu smlouvy zpětného volání.  
  
- Vytvořte instanci třídy implementace kontraktu zpětného volání a použijte ji k vytvoření objektu, <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> který předáte konstruktoru klienta WCF.  
  
- Vyvolat operace a zpracování operace zpětná volání.  
  
 Duplexní WCF klientské objekty fungují jako jejich protějšky bez duplexní, s výjimkou, že zveřejňují funkce nezbytné pro podporu zpětná volání, včetně konfigurace služby zpětného volání.  
  
 Můžete například řídit různé aspekty chování objektu zpětného volání <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> pomocí vlastností atributu ve třídě zpětného volání. Dalším příkladem je použití <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> třídy povolit vrácení informací o výjimce do služeb, které volají objekt zpětného volání. Další informace naleznete v tématu [Duplex Services](./feature-details/duplex-services.md). Kompletní ukázku naleznete v tématu [Duplex](./samples/duplex.md).  
  
 V počítačích se systémem Windows XP se službou Internet Ovou službou (IIS) 5.1 musí duplexní klienti zadat adresu klienta pomocí <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> třídy nebo je vyvolána výjimka. Následující příklad kódu ukazuje, jak to udělat v kódu.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Následující kód ukazuje, jak to udělat v konfiguračním souboru  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Volání služeb asynchronně  
 Způsob volání operací je zcela na vývojáři klienta. Důvodem je, že zprávy, které tvoří operaci lze mapovat na synchronní nebo asynchronní metody, pokud jsou vyjádřeny ve spravovaném kódu. Proto pokud chcete vytvořit klienta, který volá operace asynchronně, můžete použít Svcutil.exe generovat asynchronní kód klienta pomocí možnosti. `/async` Další informace naleznete v [tématu How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Volání služeb pomocí klientských kanálů WCF  
 WCF typy <xref:System.ServiceModel.ClientBase%601>klientů rozšířit , <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> který sám je odvozen z rozhraní vystavit základní kanál systému. Služby můžete vyvolat pomocí cílové smlouvy <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> o poskytování služeb s třídou. Podrobnosti naleznete v [tématu WCF Client Architecture](./feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
