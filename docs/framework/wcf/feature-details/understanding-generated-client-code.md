---
title: Principy generovaného klientského kódu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: dedfa55cb7be7eed396c897dedc6bf375c34436e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626266"
---
# <a name="understanding-generated-client-code"></a>Principy generovaného klientského kódu
[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vygeneruje kód klienta a konfiguračního souboru aplikace klienta pro použití při vytváření klientských aplikací. Toto téma poskytuje přehled příklady generovaného kódu pro scénáře, kontrakt služby standard. Další informace o vytváření klientských aplikací, který pomocí generovaného kódu najdete v tématu [přehled klientů WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Přehled  
 Pokud používáte sadu Visual Studio generovat klientské typy Windows Communication Foundation (WCF) pro váš projekt, obvykle není potřeba zkoumání kódu generovaného klienta. Pokud nepoužíváte prostředí pro vývoj, který provede stejné služby za vás, můžete použít nástroje, jako je Svcutil.exe generování kódu klienta a pak pomocí tohoto kódu pro vývoj klientské aplikace.  
  
 Protože Svcutil.exe má řadu možností, které upravují generovaný typ informací, toto téma nepopisuje všechny scénáře. Následující standardní úkoly zahrnují vyhledání generovaného kódu:  
  
- Identifikace rozhraní kontraktu služby.  
  
- Identifikační třída klienta WCF.  
  
- Určení datové typy.  
  
- Identifikace kontrakty zpětného volání pro duplexní služby.  
  
- Identifikace rozhraní pomocné rutiny servisní smlouvy kanálu.  
  
### <a name="finding-service-contract-interfaces"></a>Zjištění rozhraní kontraktu služby  
 Vyhledejte rozhraní, které modelují kontraktů služby, vyhledáte rozhraní, které jsou označeny <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atribut. Tento atribut často může být obtížné vyhledat s rychlým číst z důvodu přítomnosti dalších atributů a explicitní vlastnosti nastavené u samotného atributu. Mějte na paměti, že rozhraní servisní smlouvy a smlouvy rozhraní klienta jsou dva různé typy. Následující příklad kódu ukazuje původní kontrakt služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 Následující příklad kódu ukazuje stejný kontrakt služby generovaná Svcutil.exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Můžete použít rozhraní vygenerovaný servisní smlouvy spolu s <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> třídy za účelem vytvoření kanálu objekt WCF, pomocí kterého se má vyvolat operace služby. Další informace najdete v tématu [jak: Používání ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Hledání třídy klienta WCF  
 Najít třídu klienta WCF, která implementuje kontrakt služby, kterou chcete použít, vyhledejte rozšíření <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, kde parametr typu kontraktu služby rozhraní, které jste dříve sídlo a, který rozšiřuje rozhraní. Následující příklad kódu ukazuje <xref:System.ServiceModel.ClientBase%601> třídu typu `ISampleService`.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Tato třída klienta WCF můžete použít novou instanci vytvořením a voláním metody, které implementuje. Tyto metody volat operace služby, pomocí kterého je navržené a nakonfigurované k interakci. Další informace najdete v tématu [přehled klientů WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
>  SvcUtil.exe vygeneruje třídy klienta WCF, přidá <xref:System.Diagnostics.DebuggerStepThroughAttribute> do třídy klienta, která zabrání ladicí programy z krokování třída klienta WCF.  
  
### <a name="finding-data-types"></a>Vyhledávání datové typy  
 Vyhledejte datové typy ve vygenerovaném kódu, je nejzákladnější mechanismus identifikovat uvedených ve smlouvě o název typu a vyhledávání kódu pro deklaraci tohoto typu. Například následující kontrakt Určuje, že `SampleMethod` může vrátit chybu protokolu SOAP typu `microsoft.wcf.documentation.SampleFault`.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 Hledání `SampleFault` vyhledá následující deklaraci typu.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 V tomto případě datový typ je typ podrobností vyvolané určité výjimky na straně klienta <xref:System.ServiceModel.FaultException%601> kde je parametr typu podrobností `microsoft.wcf.documentation.SampleFault`. Další informace o datových typech najdete v tématu [zadání přenosu dat v kontraktech služeb](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Další informace o zpracování výjimek v klientech najdete v tématu [odesílání a příjem chyb](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Vyhledání kontrakty zpětného volání pro duplexní služby  
 Pokud se vám najít kontraktu služby, pro kterou rozhraní kontraktu Určuje hodnotu <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> vlastnost a potom tento kontrakt určuje duplexního kontraktu. Vyžadovat klientské aplikaci vytvořit třídu zpětné volání, která implementuje tento kontrakt zpětného volání a předejte instanci této třídy pro duplexní kontrakty <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> nebo <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> používaný ke komunikaci se službou. Další informace o duplexní klientů najdete v tématu [jak: Přístup ke službám pomocí duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).  
  
 Následující kontrakt určuje kontrakt zpětného volání typu `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Hledání pro tuto kontrakt zpětného volání vyhledá následující klientská aplikace musí implementovat rozhraní.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Rozhraní kanálu kontraktu služby hledání  
 Při použití <xref:System.ServiceModel.ChannelFactory> třídy pomocí rozhraní kontraktu služby, musíte přetypovat <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> rozhraní explicitně otevření, zavření nebo přerušení kanálu. Aby bylo snazší pracovat, nástroje Svcutil.exe také vygeneruje rozhraní pomocné rutiny, která implementuje oba rozhraní servisní smlouvy a <xref:System.ServiceModel.IClientChannel> umožňuje interakci s vaší stávající infrastrukturou kanálu klienta bez nutnosti přetypování. Následující kód znázorňuje definici kanálu pomocné rutiny klienta, který implementuje předchozí kontrakt služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled klientů WCF](../../../../docs/framework/wcf/wcf-client-overview.md)
