---
title: "Publikování metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- meatadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86d9eb8e7e7c78f091deea55322cbef6e6d0f3c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="publishing-metadata"></a>Publikování metadat
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]služby publikování metadat tím, že publikujete jeden nebo více koncových bodů metadat. Publikování metadat služby zpřístupňuje metadata použitím standardizovaných protokolů, jako jsou žádosti o služby WS-MetadataExchange (MEX) a protokolu HTTP nebo získat. Koncové body metadat jsou podobná další koncové body služby v, že mají adresy, vazby a kontraktu a mohou být přidány do hostitele služby prostřednictvím konfigurace nebo imperativní kódu.  
  
## <a name="publishing-metadata-endpoints"></a>Publikování kocových bodů metadat  
 Publikování kocových bodů metadat pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, je nejprve nutné přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> služby chování ke službě. Přidání <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> instance umožňuje službě vystavit koncové body metadat. Jakmile přidáte <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> chování služby, můžete pak vystavit koncové body metadat, které podporují protokol MEX nebo které reagují na požadavky HTTP/GET.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Používá <xref:System.ServiceModel.Description.WsdlExporter> pro export metadat pro všechny koncové body služby ve službě. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Export metadat ze služby, najdete v části [export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Přidá <xref:System.ServiceModel.Description.ServiceMetadataExtension> instance jako rozšíření na hostiteli služby. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Poskytuje implementaci pro publikování protokoly metadat. Můžete také použít <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> se získat metadata služby za běhu přímým přístupem <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> vlastnost.  
  
### <a name="mex-metadata-endpoints"></a>Koncové body metadat MEX  
 Přidat koncové body metadat, které používají protokol MEX, přidat koncové body služby vaší služby hostitele, který použít `IMetadataExchange` kontrakt služby. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zahrnuje <xref:System.ServiceModel.Description.IMetadataExchange> rozhraní se tento název kontraktu služby, který můžete použít jako součást [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programovací model. Koncové body služby WS-MetadataExchange, nebo MEX koncových bodů, můžete použít jednu z čtyři výchozí vazby, které metody statické factory zveřejňují na <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídy tak, aby odpovídala výchozí vazby používané [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nástroje, jako je Svcutil.exe. Můžete také nakonfigurovat koncové body metadat MEX pomocí vlastní vlastní vazby.  
  
### <a name="http-get-metadata-endpoints"></a>Koncové body metadat GET protokolu HTTP  
 Chcete-li přidat koncový bod metadat do služby, která reaguje na požadavky HTTP/GET, nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost na <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> k `true`. Můžete také nakonfigurovat metadata koncový bod, který používá protokol HTTPS nastavením <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> vlastnost <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> k `true`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Ukazuje, jak nakonfigurovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby publikovat metadata, aby klienti mohou získat metadata pomocí protokolu WS-MetadataExchange nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu.  
  
 [Postupy: Publikování metadat služby promocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Ukazuje, jak povolit publikování metadat pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby v kódu tak, aby klienti mohou získat metadata pomocí protokolu WS-MetadataExchange nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Viz také  
 [Export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
