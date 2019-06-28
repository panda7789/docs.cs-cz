---
title: Publikování metadat
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
ms.openlocfilehash: 54ab05f32320f3084fc609d8107f2892ffe6efbd
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424581"
---
# <a name="publishing-metadata"></a>Publikování metadat
Služby Windows Communication Foundation (WCF) měla být zveřejněna metadata a publikovat jednu nebo víc koncových bodů metadat. Publikování metadat služby zpřístupňuje metadata použitím standardizovaných protokolů, jako jsou žádosti o WS-MetadataExchange (MEX) a protokolu HTTP/GET. Koncové body metadat se podobně jako ostatní koncové body služby mají adresa, vazba a kontrakt a je možné je přidat k hostiteli služby prostřednictvím konfigurace nebo imperativního kódu.  
  
## <a name="publishing-metadata-endpoints"></a>Publikování kocových bodů metadat  
 Publikování koncových bodů metadat pro služby WCF, je nejprve nutné přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> služeb chování ve službě. Přidání <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> instance umožňuje službě zpřístupňují koncové body metadat. Jakmile přidáte <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> chování služby, můžete pak zveřejnit koncové body metadat, která podporují protokol MEX nebo které reagují na požadavky HTTP/GET.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Používá <xref:System.ServiceModel.Description.WsdlExporter> pro export metadat pro všechny koncové body služby ve své službě. Další informace o exportu metadat ze služby najdete v tématu [pro export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Přidá <xref:System.ServiceModel.Description.ServiceMetadataExtension> instance jako rozšíření hostitele služby. <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> Poskytuje implementaci pro publikování protokoly metadat. Můžete také použít <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> se získat metadata služby za běhu díky přístupu do <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> vlastnost.  
  
### <a name="mex-metadata-endpoints"></a>MEX koncové body metadat  
 Chcete-li přidat koncové body metadat, které používají protokol MEX, přidat koncové body služby na hostitele služby, použít `IMetadataExchange` kontrakt služby. Zahrnuje WCF <xref:System.ServiceModel.Description.IMetadataExchange> rozhraní s tímto názvem kontraktu služby, který slouží jako součást programovacího modelu WCF. Koncové body WS-MetadataExchange, nebo na koncové body MEX, můžete použít jednu z poskytující metody pro vytváření statických objektů na čtyři výchozí vazby <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídy tak, aby odpovídaly výchozím vazbám používat WCF nástroje, jako je například Svcutil.exe. Můžete taky nakonfigurovat pomocí vlastního vlastní vazby MEX koncové body metadat.  
  
### <a name="http-get-metadata-endpoints"></a>Koncové body metadat GET protokolu HTTP  
 Chcete-li přidat koncový bod metadat do svojí služby, který reaguje na požadavky HTTP/GET, nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> k `true`. Můžete taky nakonfigurovat koncový bod metadat, který používá protokol HTTPS tak, že nastavíte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> vlastnost <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> k `true`.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Ukazuje, jak nakonfigurovat tak, aby klienti mohou získat metadata pomocí WS-MetadataExchange nebo pomocí požadavku HTTP/GET být zveřejněna metadata služby WCF `?wsdl` řetězec dotazu.  
  
 [Postupy: Publikování metadat služby promocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Ukazuje, jak povolit publikování metadat služby WCF v kódu tak, aby klienti mohou získat metadata pomocí WS-MetadataExchange nebo pomocí požadavku HTTP/GET `?wsdl` řetězec dotazu.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Viz také:

- [Export a import metadat](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
