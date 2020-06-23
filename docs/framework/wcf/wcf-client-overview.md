---
title: Klienti WCF – přehled
description: Přečtěte si, co dělají klientské aplikace, jak konfigurovat, vytvářet a používat klienta WCF a jak zabezpečit klientské aplikace.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: c66541f95d04373a9a29fafe58528872335936c4
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245906"
---
# <a name="wcf-client-overview"></a>Přehled klientů WCF

Tato část popisuje, co dělají klientské aplikace, jak konfigurovat, vytvářet a používat klienta Windows Communication Foundation (WCF) a jak zabezpečit klientské aplikace.  
  
## <a name="using-wcf-client-objects"></a>Použití objektů klienta WCF  
 Klientská aplikace je spravovaná aplikace, která používá klienta WCF ke komunikaci s jinou aplikací. Vytvoření klientské aplikace pro službu WCF vyžaduje následující kroky:  
  
1. Získání kontraktu služby, vazeb a informací o adrese pro koncový bod služby.  
  
2. Pomocí těchto informací vytvořte klienta WCF.  
  
3. Operace volání.  
  
4. Zavřete objekt klienta WCF.  
  
Následující části popisují tyto kroky a poskytují stručný úvod k následujícím problémům:  
  
- Zpracování chyb.  
  
- Konfigurace a zabezpečení klientů.  
  
- Vytváření objektů zpětného volání pro duplexní služby.  
  
- Asynchronní volání služeb  
  
- Volání služeb pomocí kanálů klienta.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Získání kontraktu služby, vazeb a adres  
 Služba WCF, služby a klienti modelují kontrakty pomocí spravovaných atributů, rozhraní a metod. Chcete-li se připojit ke službě v klientské aplikaci, je třeba získat informace o typu pro kontrakt služby. Obvykle získáte informace o typu pro kontrakt služby pomocí nástroje pro dodávání [metadat ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md). Nástroj stáhne metadata ze služby, převede ji na spravovaný soubor zdrojového kódu v jazyce podle vašeho výběru a vytvoří konfigurační soubor klientské aplikace, který můžete použít ke konfiguraci objektu klienta služby WCF. Například pokud chcete vytvořit objekt klienta WCF k vyvolání a `MyCalculatorService` víte, že metadata pro tuto službu jsou publikována v `http://computerName/MyCalculatorService/Service.svc?wsdl` , následující příklad kódu ukazuje, jak použít Svcutil.exe k získání `ClientCode.vb` souboru, který obsahuje kontrakt služby ve spravovaném kódu.  
  
```console  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 Tento kód smlouvy můžete buď zkompilovat do klientské aplikace nebo do jiného sestavení, které může klientská aplikace použít k vytvoření objektu klienta WCF. Konfigurační soubor můžete použít ke konfiguraci objektu klienta pro správné připojení ke službě.  
  
 Příklad tohoto procesu najdete v tématu [Postupy: Vytvoření klienta](how-to-create-a-wcf-client.md). Další informace o smlouvách najdete v tématu [kontrakty](./feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Vytvoření objektu klienta WCF  
 Klient služby WCF je místní objekt, který představuje službu WCF ve formě, kterou může klient použít ke komunikaci se vzdálenou službou. Typy klientů WCF implementují cílový kontrakt služby, takže když ho vytvoříte a nakonfigurujete, můžete objekt klienta použít přímo k vyvolání operací služby. Čas běhu služby WCF převede volání metody do zpráv, odesílá je do služby, naslouchá odpovědi a vrátí tyto hodnoty objektu klienta služby WCF jako návratové hodnoty nebo `out` `ref` parametry.  
  
 Můžete také použít objekty kanálu klienta WCF pro připojení ke službám a jejich používání. Podrobnosti najdete v tématu [Architektura klienta WCF](./feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Vytvoření nového objektu WCF  
 Pro ilustraci použití <xref:System.ServiceModel.ClientBase%601> třídy Předpokládejme, že následující jednoduchý kontrakt služby byl vygenerován z aplikace služby.  
  
> [!NOTE]
> Pokud používáte aplikaci Visual Studio k vytvoření klienta služby WCF, objekty jsou automaticky načteny do prohlížeče objektů při přidání odkazu na službu do projektu.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Pokud nepoužíváte aplikaci Visual Studio, Projděte si kód generovaného kontraktu a vyhledejte typ, který rozšiřuje <xref:System.ServiceModel.ClientBase%601> a rozhraní kontraktu služby `ISampleService` . V tomto případě vypadá tento typ jako následující kód:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Tato třída může být vytvořena jako místní objekt pomocí jednoho z konstruktorů, nakonfigurovaných a pak slouží pro připojení ke službě typu `ISampleService` .  
  
 Doporučuje se nejprve vytvořit objekt klienta WCF a pak ho použít a zavřít v rámci jednoho bloku try/catch. Nepoužívejte `using` příkaz ( `Using` v Visual Basic), protože může maskovat výjimky v určitých režimech selhání. Další informace najdete v následujících částech a také v tématu [ukončení a přerušení pro vydání prostředků klienta WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Kontrakty, vazby a adresy  
 Předtím, než můžete vytvořit objekt klienta WCF, je nutné nakonfigurovat objekt klienta. Konkrétně musí mít *koncový bod* služby, který se má použít. Koncový bod je kombinací kontraktu služby, vazby a adresy. (Další informace o koncových bodech najdete v tématu [koncové body: adresy, vazby a kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).) Obvykle se tyto informace nacházejí v [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-of-client.md) prvku v konfiguračním souboru klientské aplikace, jako je například ten, který nástroj Svcutil.exe vygeneruje, a je automaticky načten při vytváření objektu klienta. Oba typy klientů WCF mají také přetížení, která umožňují programové zadání těchto informací.  
  
 Například vygenerovaný konfigurační soubor pro `ISampleService` použití v předchozích příkladech obsahuje následující informace o koncovém bodu.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Tento konfigurační soubor určuje cílový koncový bod v `<client>` elementu. Další informace o použití více cílových koncových bodů naleznete v tématu <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> konstruktory nebo.  
  
## <a name="calling-operations"></a>Operace volání  
 Jakmile vytvoříte a nakonfigurujete objekt klienta, vytvořte blok try/catch, operace volání stejným způsobem, jako kdyby byl objekt místní, a zavřete objekt klienta WCF. Když klientská aplikace volá první operaci, služba WCF automaticky otevře příslušný kanál a podkladový kanál se zavře, když se objekt recykluje. (Nebo můžete také explicitně otevřít a zavřít kanál před nebo po volání jiných operací.)  
  
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
  
 Můžete volat operace vytvořením objektu klienta WCF a voláním jeho metod, jak ukazuje následující příklad kódu. Otevření, volání a zavření objektu klienta služby WCF probíhá v rámci jednoho bloku try/catch. Další informace najdete v tématu [přístup ke službám pomocí klienta WCF](./feature-details/accessing-services-using-a-client.md) a [použití funkcí zavřít a přerušit k vydání prostředků klienta WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Zpracování chyb  
 Výjimky mohou nastat v klientské aplikaci při otevírání základního kanálu klienta (ať už explicitně nebo automaticky voláním operace), pomocí objektu klienta nebo kanálu pro volání operací nebo při zavírání podkladového klientského kanálu. Doporučuje se přinejmenším to, aby aplikace čekaly na možné <xref:System.TimeoutException?displayProperty=nameWithType> a <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> výjimky kromě jakýchkoli <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objektů vyvolaných v důsledku chyb protokolu SOAP vrácených operacemi. Chyby protokolu SOAP zadané v kontraktu operace jsou vyvolány klientským aplikacím jako v případě, že <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> parametr typu je detailní typ chyby protokolu SOAP. Další informace o manipulaci s chybovými stavy v klientské aplikaci najdete v tématu [odesílání a příjem chyb](sending-and-receiving-faults.md). Kompletní vzorek ukazuje, jak zpracovávat chyby v klientovi, najdete v tématu [očekávané výjimky](./samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Konfigurace a zabezpečení klientů  
 Konfigurace klienta začíná načtením informací cílového koncového bodu pro objekt klienta nebo kanálu, obvykle z konfiguračního souboru, i když můžete tyto informace programově načíst pomocí konstruktorů a vlastností klienta. Další konfigurační kroky jsou ale potřeba k tomu, aby se povolilo určité chování klienta a mnoho scénářů zabezpečení.  
  
 Například požadavky na zabezpečení pro kontrakty služby jsou deklarovány v rozhraní kontraktu služby a pokud Svcutil.exe vytvořili konfigurační soubor, tento soubor obvykle obsahuje vazbu, která podporuje požadavky na zabezpečení služby. V některých případech ale může být nutná další konfigurace zabezpečení, například konfigurace přihlašovacích údajů klienta. Úplné informace o konfiguraci zabezpečení pro klienty WCF najdete v tématu [zabezpečení klientů](securing-clients.md).  
  
 Kromě toho je možné v klientských aplikacích povolit některé vlastní úpravy, jako je například vlastní chování při běhu. Další informace o tom, jak nakonfigurovat vlastní chování klienta, najdete v tématu [Konfigurace chování klienta](configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Vytváření objektů zpětného volání pro duplexní služby  
 Duplexní služby určují kontrakt zpětného volání, který musí klientská aplikace implementovat, aby poskytovala objekt zpětného volání, který by služba volala podle požadavků smlouvy. I když objekty zpětného volání nejsou úplné služby (například nelze iniciovat kanál s objektem zpětného volání) pro účely implementace a konfigurace, které lze představit jako typ služby.  
  
 Klienti duplexních služeb musí:  
  
- Implementujte třídu kontraktu zpětného volání.  
  
- Vytvořte instanci třídy implementace kontraktu zpětného volání a použijte ji k vytvoření <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> objektu, který předáte do konstruktoru klienta WCF.  
  
- Vyvolat operace a zpracovávat zpětná volání operací.  
  
 Duplexní objekty klienta WCF fungují stejně jako jejich neduplexní protějšky s výjimkou, že zpřístupňují funkce potřebné pro podporu zpětného volání, včetně konfigurace služby zpětného volání.  
  
 Můžete například řídit různé aspekty chování za běhu objektů zpětného volání pomocí vlastností <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> atributu třídy zpětného volání. Dalším příkladem je použití <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> třídy, která umožňuje vrátit informace o výjimce službám, které volají objekt zpětného volání. Další informace najdete v tématu [duplexní služby](./feature-details/duplex-services.md). Úplnou ukázku najdete v tématu [duplexní režim](./samples/duplex.md).  
  
 V počítačích se systémem Windows XP se systémem Internetová informační služba (IIS) 5,1 musí duplexní klienti zadat základní adresu klienta pomocí <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> třídy nebo je vyvolána výjimka. Následující příklad kódu ukazuje, jak to provést v kódu.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Následující kód ukazuje, jak to provést v konfiguračním souboru.  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Asynchronní volání služby  
 Způsob volání operací je zcela až ke klientskému vývojáři. Důvodem je, že zprávy, které tvoří operaci, lze namapovat na synchronní nebo asynchronní metody, pokud jsou vyjádřeny ve spravovaném kódu. Proto pokud chcete vytvořit klienta, který volá operace asynchronně, můžete použít Svcutil.exe k vygenerování kódu asynchronního klienta pomocí `/async` Možnosti. Další informace najdete v tématu [Postupy: asynchronní volání operací služby](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Volání služeb pomocí kanálů klientů WCF  
 Typy klientů WCF rozšiřuje <xref:System.ServiceModel.ClientBase%601> , které jsou odvozeny z <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> rozhraní a zpřístupňují základní systém kanálu. Služby můžete vyvolat pomocí cílové kontraktu služby s <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> třídou. Podrobnosti najdete v tématu [Architektura klienta WCF](./feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
