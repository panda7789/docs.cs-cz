---
title: Publikování a načítání metadat prostřednictvím vlastní vazby
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 33777358262465e9ecbadd75df8abf066bafcd01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991208"
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Publikování a načítání metadat prostřednictvím vlastní vazby
<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Poskytuje podporu pro přidání koncový bod metadat služby. Tyto koncové body metadat můžou reagovat na požadavky HTTP GET na adresu URL, která má `?wsdl` querystring a k přenosu WS požadavky metody GET jak je definováno ve specifikaci WS-MetadataExchange (MEX). Koncové body MEX implementovat <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> kontraktu.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Publikování metadat prostřednictvím vlastní vazby  
 Koncové body metadat GET protokolu HTTP a HTTPS GET koncové body metadat se povoluje nastavením <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> vlastností `true`. Vazby pro tyto koncové body se nedá nakonfigurovat.  
  
 <xref:System.ServiceModel.Description.IMetadataExchange> Smlouvy, ale je možné s jakýmkoli koncovým bodem, včetně těch, které používají vlastní vazby, protože <xref:System.ServiceModel.Description.IMetadataExchange> koncové body jsou stejné pro všechny ostatní služby Windows Communication Foundation (WCF) koncového bodu služby. Pokud víte, jak upravit konfiguraci vazeb poskytovaných systémem nebo víte, jak nakonfigurovat <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, pak můžete nakonfigurovat vazby pro použití s <xref:System.ServiceModel.Description.IMetadataExchange> koncového bodu.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Načítání metadat prostřednictvím vlastní vazby  
 Metadata mohou být načteny z Get protokolu HTTP a HTTPS Get koncové body metadat pomocí standardní požadavků protokolu HTTP nebo HTTPS GET.  
  
 K načtení metadat z koncových bodů metadat MEX můžete obvykle použít jednu z standardní vazby MEX podporuje WCF. Další informace naleznete v tématu <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Typu a nástroje Svcutil.exe automaticky vybrat jeden z těchto standardních MEX vazeb na základě adresy koncového bodu Zadaná metadata.  
  
 Pokud koncový bod metadat MEX používá jinou vazbou než standardní vazby MEX, můžete nakonfigurovat vazby používá <xref:System.ServiceModel.Description.MetadataExchangeClient> pomocí kódu nebo za poskytování <xref:System.ServiceModel.Description.IMetadataExchange> konfigurace koncového bodu klienta. Nástroje Svcutil.exe automaticky načte z konfiguračního souboru <xref:System.ServiceModel.Description.IMetadataExchange> klienta konfigurace koncového bodu, který má stejný název jako schéma identifikátoru URI pro adresu koncového bodu metadat.  
  
## <a name="security"></a>Zabezpečení  
 Při publikování metadat prostřednictvím vlastní vazby, ujistěte se, že vazba poskytuje podporu zabezpečení, kterou vyžaduje vaše metadata. Například, zpřístupnění informací zabránit a zajistit váš klient má oprávnění získat metadata, můžete nastavit metadata a vaše aplikace lépe zabezpečit tím, že nakonfigurujete vaše <xref:System.ServiceModel.Description.IMetadataExchange> koncový bod tak, aby vyžadovala ověřování a šifrování. Ukázka [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) ukazuje tento scénář.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení služeb](../../../../docs/framework/wcf/securing-services.md)
- [Vazby WS-MetadataExchange](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)
- [Postupy: Konfigurace vlastního protokolu WS-Metadata Exchange vazby](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [Postupy: Načítání metadat přes vazbu jiného typu než MEX](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
