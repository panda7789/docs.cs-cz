---
title: Principy generovaného klientského kódu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 6bc921355e54023ead3a308a7877ab609f868221
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968624"
---
# <a name="understanding-generated-client-code"></a>Principy generovaného klientského kódu
Nástroj pro dodávání [metadat (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vygeneruje klientský kód a konfigurační soubor klientské aplikace pro použití při sestavování klientských aplikací. Toto téma poskytuje ukázku generovaných příkladů kódu pro scénáře standardních kontraktů služeb. Další informace o vytváření klientských aplikací pomocí vygenerovaného kódu naleznete v tématu [Přehled klientů WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Přehled  
 Použijete-li aplikaci Visual Studio k vygenerování typů klientů Windows Communication Foundation (WCF) pro váš projekt, obvykle není nutné kontrolovat generovaný kód klienta. Pokud nepoužíváte vývojové prostředí, které pro vás provádí stejné služby, můžete pomocí nástroje, jako je Svcutil. exe, vygenerovat kód klienta a potom použít tento kód k vývoji klientské aplikace.  
  
 Vzhledem k tomu, že Svcutil. exe má několik možností, které upravují informace o vygenerovaném typu, toto téma se nezabývá všemi scénáři. Následující standardní úlohy však zahrnují umístění vygenerovaného kódu:  
  
- Identifikujte rozhraní kontraktu služby.  
  
- Identifikace třídy klienta WCF.  
  
- Identifikace datových typů.  
  
- Identifikujte kontrakty zpětného volání pro duplexní služby.  
  
- Identifikujte rozhraní kanálu smlouvy pomocné služby.  
  
### <a name="finding-service-contract-interfaces"></a>Hledání rozhraní kontraktu služby  
 Chcete-li vyhledat rozhraní, která modelují kontrakty služby, vyhledejte rozhraní, která <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> jsou označena atributem. Tento atribut často může být obtížné vyhledat s rychlým čtením z důvodu přítomnosti jiných atributů a explicitních vlastností nastavených u atributu samotného. Mějte na paměti, že rozhraní kontraktu služby a klientské rozhraní klienta jsou dva různé typy. Následující příklad kódu ukazuje původní kontrakt služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 Následující příklad kódu ukazuje stejný kontrakt služby, jak je vygenerován nástrojem Svcutil. exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Pomocí vygenerovaného rozhraní <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> kontraktu služby můžete vytvořit objekt kanálu WCF, se kterým chcete vyvolat operace služby. Další informace najdete v tématu [jak: Použijte třídu ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Hledání tříd klienta WCF  
 Chcete-li vyhledat třídu klienta WCF, která implementuje kontrakt služby, který chcete použít, vyhledejte rozšíření <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, kde parametr Type je rozhraní kontraktu služby, které jste předtím našli a které rozšiřuje toto rozhraní. Následující příklad kódu ukazuje <xref:System.ServiceModel.ClientBase%601> třídu typu. `ISampleService`  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Tuto třídu klienta WCF můžete použít vytvořením nové instance a voláním metod, které implementuje. Tyto metody vyvolávají operaci služby, se kterou je navržená a nakonfigurovaná pro interakci. Další informace najdete v tématu [Přehled klientů WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
> Když Svcutil. exe vygeneruje třídu klienta WCF, přidá <xref:System.Diagnostics.DebuggerStepThroughAttribute> do třídy Client, která brání ladicím programům v procházení klientské třídy WCF.  
  
### <a name="finding-data-types"></a>Hledání datových typů  
 Chcete-li vyhledat datové typy ve vygenerovaném kódu, je nejzákladnější mechanismus identifikovat název typu zadaný ve kontraktu a vyhledat kód pro danou deklaraci typu. Například následující kontrakt Určuje, že `SampleMethod` může vrátit chybu SOAP typu. `microsoft.wcf.documentation.SampleFault`  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 `SampleFault` Hledání vyhledá následující deklaraci typu.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 V tomto případě datový typ je typ podrobností vyvolaný specifickou výjimkou u klienta, <xref:System.ServiceModel.FaultException%601> přičemž parametr detailního typu je. `microsoft.wcf.documentation.SampleFault` Další informace o datových typech najdete v tématu [určení přenos dat v kontraktech služeb](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Další informace o zpracování výjimek v klientech najdete v tématu [odesílání a příjem chyb](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Hledání kontraktů zpětného volání pro duplexní služby  
 Pokud najdete kontrakt služby, pro který rozhraní kontraktu Určuje hodnotu <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> vlastnosti, pak tato smlouva určuje oboustranný kontrakt. Duplexní kontrakty vyžadují, aby klientská aplikace vytvořila třídu zpětného volání, která implementuje kontrakt zpětného volání, a <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> předala instanci této třídy do nebo <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> , která se používá ke komunikaci se službou. Další informace o oboustranných klientech najdete [v tématu How to: Přístup ke službám pomocí duplexního](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)kontraktu.  
  
 Následující kontrakt Určuje kontrakt zpětného volání typu `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Hledání této smlouvy zpětného volání vyhledá následující rozhraní, které musí klientská aplikace implementovat.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Hledání rozhraní kanálu kontraktu služby  
 Při použití <xref:System.ServiceModel.ChannelFactory> třídy s rozhraním kontraktu služby je nutné přetypovat <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> na rozhraní, aby bylo možné explicitně otevřít, zavřít nebo přerušit kanál. Aby bylo snazší pracovat s nástrojem, nástroj Svcutil. exe také generuje pomocné rozhraní, které implementuje rozhraní kontraktu služby, a <xref:System.ServiceModel.IClientChannel> umožňuje interakci s infrastrukturou kanálu klienta bez nutnosti přetypování. Následující kód ukazuje definici kanálu pomocníka klienta, který implementuje předchozí kontrakt služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled klientů WCF](../../../../docs/framework/wcf/wcf-client-overview.md)
