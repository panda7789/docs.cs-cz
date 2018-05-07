---
title: Principy generovaného klientského kódu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 8a28b52d786793308d8609704b564b75f23d95d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="understanding-generated-client-code"></a>Principy generovaného klientského kódu
[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generuje kód klienta a konfigurační soubor aplikace klienta pro použití při vytváření klientské aplikace. Toto téma obsahuje přehled používání příklady generovaný kód pro scénáře kontraktu služby na úrovni standard. Další informace o vytváření klientských aplikací pomocí generovaného kódu najdete v tématu [klienta WCF – přehled](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Přehled  
 Pokud používáte Visual Studio k vygenerování typů klientů Windows Communication Foundation (WCF) pro svůj projekt, obvykle není potřeba kontrola kódu generovaného klienta. Pokud nepoužíváte vývojového prostředí, které provádí stejné služby pro vás, můžete generovat kód klienta a pak pomocí tohoto kódu k vývoji klientskou aplikaci nástroje, jako je Svcutil.exe.  
  
 Protože Svcutil.exe má několik možností, které upravte informace generované typu, toto téma nepopisuje všechny scénáře. Následující úlohy standardní zahrnují vyhledání generovaného kódu:  
  
-   Identifikace rozhraní kontraktu služby.  
  
-   Identifikační třída klienta WCF.  
  
-   Identifikace datové typy.  
  
-   Identifikace kontrakty zpětného volání pro duplexní služby.  
  
-   Identifikace rozhraní pomocná kontraktu služby kanálu.  
  
### <a name="finding-service-contract-interfaces"></a>Rozhraní kontraktu služby hledání  
 Chcete-li vyhledat rozhraní, která modelu kontrakty služeb, vyhledejte rozhraní, které jsou označené <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atribut. Tento atribut často může být obtížné vyhledat s rychlým číst z důvodu přítomnosti dalších atributů a explicitní vlastnosti, které jsou nastaveny na atribut sám sebe. Mějte na paměti, že rozhraní kontraktu služby a rozhraní kontraktu klienta jsou dva různé typy. Následující příklad kódu ukazuje na původní kontrakt služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 Následující příklad kódu ukazuje na stejné kontrakt služby generovaná Svcutil.exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Můžete použít rozhraní kontrakt generovaný služby spolu s <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> třída vytvořte objekt kanálu WCF se kterým má být vyvolán operací služby. Další informace najdete v tématu [postupy: použití třídy ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Hledání třídy klienta WCF  
 Chcete-li najít třídu klienta WCF, která implementuje kontrakt služby, kterou chcete použít, vyhledejte rozšíření <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, kde parametr typu je kontrakt služby rozhraní, kterou jste dříve nachází, a který rozšiřuje tohoto rozhraní. Následující příklad kódu ukazuje <xref:System.ServiceModel.ClientBase%601> – třída typu `ISampleService`.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Tato třída klienta WCF můžete vytvořit novou instanci a volání metod, které implementuje. Tyto metody vyvolání operace služby, pomocí kterého je navržena a nakonfigurovat tak, aby komunikovat. Další informace najdete v tématu [klienta WCF – přehled](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
>  Pokud SvcUtil.exe vygeneruje třídy klienta WCF, přidá <xref:System.Diagnostics.DebuggerStepThroughAttribute> k třídě klienta, která zabraňuje ladicí programy z procházení třída klienta WCF.  
  
### <a name="finding-data-types"></a>Hledání datové typy  
 Datové typy vyhledat v generovaného kódu, je nejzákladnější mechanismus určit název typu uvedených ve smlouvě a vyhledat kód pro tento typ deklarace. Například následující kontrakt Určuje, že `SampleMethod` může vrátit chybu protokolu SOAP typu `microsoft.wcf.documentation.SampleFault`.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 Hledání `SampleFault` vyhledá následující deklaraci typu.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 V takovém případě datový typ je typ podrobností vyvolané určité výjimky na straně klienta <xref:System.ServiceModel.FaultException%601> kde parametr typu podrobností je `microsoft.wcf.documentation.SampleFault`. Další informace o typech dat najdete v tématu [zadání přenos dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Další informace o zpracování výjimek v klientech najdete v tématu [odesílání a přijímání chyb](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Hledání kontrakty zpětného volání pro duplexní služby  
 Pokud vyhledat kontraktu služby, pro který rozhraní kontrakt Určuje hodnotu <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> vlastnost a potom tento kontrakt určuje duplexního kontraktu. Duplexní kontrakty vyžadují klientská aplikace vytvořte třídu zpětného volání, která implementuje kontrakt zpětného volání a předat instance této třídy <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> nebo <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> používaný ke komunikaci se službou. Další informace o klientech, duplexní najdete v tématu [postupy: přístup k službám pomocí duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).  
  
 Následující kontrakt určuje kontraktu zpětného volání typu `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 Vyhledávání pro tento kontrakt zpětného volání vyhledá následující rozhraní, které musí implementovat klientské aplikace.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Kanál kontrakt služby s vyhledáním rozhraní  
 Při použití <xref:System.ServiceModel.ChannelFactory> – třída pomocí rozhraní kontraktu služby, musíte přetypovat <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> rozhraní explicitně otevřít, zavřít nebo přerušení kanál. Aby bylo snazší s ním pracovat, nástroje Svcutil.exe rovněž vygeneruje rozhraní pomocné rutiny, který implementuje rozhraní služby kontrakt rozhraní a <xref:System.ServiceModel.IClientChannel> umožnit komunikovat s infrastrukturou kanálu klienta bez nutnosti přetypovat. Následující kód ukazuje definici kanálu klienta pomocné rutiny, který implementuje předchozí kontrakt služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled klientů WCF](../../../../docs/framework/wcf/wcf-client-overview.md)
