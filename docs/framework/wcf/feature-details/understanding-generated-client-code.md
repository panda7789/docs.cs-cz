---
title: "Principy generovaného klientského kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 935f3fe168ebafd7a62c54d2aec1c8336a31a54a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="understanding-generated-client-code"></a>Principy generovaného klientského kódu
[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generuje kód klienta a konfigurační soubor aplikace klienta pro použití při vytváření klientské aplikace. Toto téma obsahuje přehled používání příklady generovaný kód pro scénáře kontraktu služby na úrovni standard. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vytvoření klientských aplikací pomocí generovaného kódu, najdete v části [klienta WCF – přehled](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Přehled  
 Pokud používáte [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ke generování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] typů klientů pro svůj projekt, obvykle není nutné prozkoumat kód klienta vygenerovaný. Pokud nepoužíváte vývojového prostředí, které provádí stejné služby pro vás, můžete generovat kód klienta a pak pomocí tohoto kódu k vývoji klientskou aplikaci nástroje, jako je Svcutil.exe.  
  
 Protože Svcutil.exe má několik možností, které upravte informace generované typu, toto téma nepopisuje všechny scénáře. Následující úlohy standardní zahrnují vyhledání generovaného kódu:  
  
-   Identifikace rozhraní kontraktu služby.  
  
-   Identifikace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] třída klienta.  
  
-   Identifikace datové typy.  
  
-   Identifikace kontrakty zpětného volání pro duplexní služby.  
  
-   Identifikace rozhraní pomocná kontraktu služby kanálu.  
  
### <a name="finding-service-contract-interfaces"></a>Rozhraní kontraktu služby hledání  
 Chcete-li vyhledat rozhraní, která modelu kontrakty služeb, vyhledejte rozhraní, které jsou označené <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atribut. Tento atribut často může být obtížné vyhledat s rychlým číst z důvodu přítomnosti dalších atributů a explicitní vlastnosti, které jsou nastaveny na atribut sám sebe. Mějte na paměti, že rozhraní kontraktu služby a rozhraní kontraktu klienta jsou dva různé typy. Následující příklad kódu ukazuje na původní kontrakt služby.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 Následující příklad kódu ukazuje na stejné kontrakt služby generovaná Svcutil.exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Můžete použít rozhraní kontrakt generovaný služby spolu s <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> třídy za účelem vytvoření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanál objektu, se kterým má být vyvolán operací služby. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: použití třídy ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Hledání třídy klienta WCF  
 Vyhledejte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta třídu, která implementuje kontrakt služby, kterou chcete použít, hledání pro rozšíření <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, kde parametr typu je kontrakt služby rozhraní, kterou jste dříve nachází, a který rozšiřuje tohoto rozhraní. Následující příklad kódu ukazuje <xref:System.ServiceModel.ClientBase%601> – třída typu `ISampleService`.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Můžete to použít [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] třída klienta vytvořením novou instanci a volání metod implementuje. Tyto metody vyvolání operace služby, pomocí kterého je navržena a nakonfigurovat tak, aby komunikovat. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Klienta WCF – přehled](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
> [!NOTE]
>  Pokud SvcUtil.exe vygeneruje třídy klienta WCF, přidá <xref:System.Diagnostics.DebuggerStepThroughAttribute> k třídě klienta, která zabraňuje ladicí programy z procházení třída klienta WCF.  
  
### <a name="finding-data-types"></a>Hledání datové typy  
 Datové typy vyhledat v generovaného kódu, je nejzákladnější mechanismus určit název typu uvedených ve smlouvě a vyhledat kód pro tento typ deklarace. Například následující kontrakt Určuje, že `SampleMethod` může vrátit chybu protokolu SOAP typu `microsoft.wcf.documentation.SampleFault`.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 Hledání `SampleFault` vyhledá následující deklaraci typu.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 V takovém případě datový typ je typ podrobností vyvolané určité výjimky na straně klienta <xref:System.ServiceModel.FaultException%601> kde parametr typu podrobností je `microsoft.wcf.documentation.SampleFault`. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]datové typy, najdete v části [zadání přenos dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]zpracování výjimek v klientech, najdete v části [odesílání a přijímání chyb](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Hledání kontrakty zpětného volání pro duplexní služby  
 Pokud vyhledat kontraktu služby, pro který rozhraní kontrakt Určuje hodnotu <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> vlastnost a potom tento kontrakt určuje duplexního kontraktu. Duplexní kontrakty vyžadují klientská aplikace vytvořte třídu zpětného volání, která implementuje kontrakt zpětného volání a předat instance této třídy <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> nebo <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> používaný ke komunikaci se službou. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]duplexní klientů naleznete v tématu [postupy: přístup k službám pomocí duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).  
  
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
 [Klienti WCF – přehled](../../../../docs/framework/wcf/wcf-client-overview.md)
