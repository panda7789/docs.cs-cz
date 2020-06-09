---
title: Publikování metadat
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
ms.openlocfilehash: 456eecde88fec182d3234c20a4f01971fd045bb8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596757"
---
# <a name="publishing-metadata"></a>Publikování metadat
Služby Windows Communication Foundation (WCF) publikují metadata publikováním jednoho nebo více koncových bodů metadat. Publikování metadat služby zpřístupňuje metadata pomocí standardizovaných protokolů, jako jsou WS-MetadataExchange (MEX) a požadavky HTTP/GET. Koncové body metadat jsou podobné jiným koncovým bodům služby v tom, že mají adresu, vazbu a kontrakt a mohou být přidány do hostitele služby prostřednictvím konfigurace nebo imperativního kódu.  
  
## <a name="publishing-metadata-endpoints"></a>Publikování kocových bodů metadat  
 K publikování koncových bodů metadat pro službu WCF musíte nejprve <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do služby Přidat chování služby. Přidáním <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> instance umožníte službě vystavit koncové body metadat. Jakmile přidáte <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> chování služby, můžete vystavit koncové body metadat, které podporují protokol MEX nebo které reagují na požadavky HTTP/GET.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>Používá <xref:System.ServiceModel.Description.WsdlExporter> k exportu metadat pro všechny koncové body služby ve vaší službě. Další informace o exportu metadat ze služby najdete v tématu [Export a import metadat](exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>Přidá <xref:System.ServiceModel.Description.ServiceMetadataExtension> instanci jako rozšíření pro hostitele služby. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType>Poskytuje implementaci pro protokoly publikování metadat. K <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> získání metadat služby za běhu můžete použít také přístup k <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> Vlastnosti.  
  
### <a name="mex-metadata-endpoints"></a>Koncové body metadat MEX  
 K přidání koncových bodů metadat, které používají protokol MEX, přidejte koncové body služby pro hostitele služby, které používají `IMetadataExchange` kontrakt služby. Služba WCF zahrnuje <xref:System.ServiceModel.Description.IMetadataExchange> rozhraní s tímto názvem kontraktu služby, které můžete použít jako součást programovacího modelu WCF. Koncové body WS-MetadataExchange nebo MEX můžou používat jednu ze čtyř výchozích vazeb, které metody statických továrnů zpřístupňují na <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídě, aby odpovídaly výchozím vazbám používaným v nástrojích WCF, jako je Svcutil. exe. Můžete taky nakonfigurovat koncové body metadat MEX pomocí vlastní vazby.  
  
### <a name="http-get-metadata-endpoints"></a>Koncové body metadat HTTP GET  
 Chcete-li ke službě přidat koncový bod metadat, který reaguje na požadavky HTTP/GET, nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost na <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> `true` . Koncový bod metadat, který používá protokol HTTPS, můžete také nakonfigurovat nastavením <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> vlastnosti na <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> `true` .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Publikování metadat služby promocí konfiguračního souboru](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Ukazuje, jak nakonfigurovat službu WCF pro publikování metadat, aby klienti mohli získat metadata pomocí WS-MetadataExchange nebo požadavku HTTP/GET pomocí `?wsdl` řetězce dotazu.  
  
 [Postupy: Publikování metadat služby promocí kódu](how-to-publish-metadata-for-a-service-using-code.md)  
 Ukazuje, jak povolit publikování metadat pro službu WCF v kódu, aby klienti mohli získat metadata pomocí WS-MetadataExchange nebo pomocí požadavku HTTP/GET pomocí `?wsdl` řetězce dotazu.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Viz také

- [Export a import metadat](exporting-and-importing-metadata.md)
