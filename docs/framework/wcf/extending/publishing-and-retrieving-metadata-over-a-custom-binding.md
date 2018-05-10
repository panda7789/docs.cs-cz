---
title: Publikování a načítání metadat prostřednictvím vlastní vazby
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 528f7662ee3a1f956427e5e42f540816f55027f8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Publikování a načítání metadat prostřednictvím vlastní vazby
<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Poskytuje podporu pro přidání koncový bod metadat do služby. Tyto koncové body metadat může reagovat na požadavky HTTP GET na adresu URL, která má `?wsdl` řetězce dotazu a požadavky metody GET přenosu WS definovaným ve specifikaci WS-MetadataExchange (MEX). Koncové body MEX implementovat <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> kontrakt.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Publikování metadat prostřednictvím vlastní vazby  
 Koncové body metadat metody GET protokolu HTTP a HTTPS získat koncové body metadat jsou povoleny nastavením <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> vlastnosti, které chcete `true`. Nelze nakonfigurovat vazby u těchto koncových bodů.  
  
 <xref:System.ServiceModel.Description.IMetadataExchange> Kontrakt, ale dá použít s žádný koncový bod, včetně těch, které používají vlastní vazby, protože <xref:System.ServiceModel.Description.IMetadataExchange> koncové body jsou stejné jako všechny ostatní Windows Communication Foundation (WCF) koncový bod služby. Pokud víte, jak změnit konfiguraci vazby poskytované systémem, nebo pokud víte, jak nakonfigurovat <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, pak můžete nakonfigurovat vazby pro použití s <xref:System.ServiceModel.Description.IMetadataExchange> koncový bod.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Načítání metadat prostřednictvím vlastní vazby  
 Nejde načíst metadata z Get protokolu HTTP a HTTPS získat metadata koncové body pomocí standardní požadavků protokolu HTTP nebo HTTPS získat.  
  
 Pro načtení metadat z koncového bodu metadat MEX obecně slouží jedna z vazeb standardní MEX podporované službou WCF. Další informace naleznete v tématu <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Typ a nástroje Svcutil.exe automaticky vyberte jednu z těchto standardní MEX vazeb na základě adresy Zadaná metadata koncového bodu.  
  
 Pokud koncový bod metadat MEX používá jinou vazbou než jedna z vazeb standardní MEX, můžete nakonfigurovat vazby používané <xref:System.ServiceModel.Description.MetadataExchangeClient> pomocí kódu nebo pomocí zadáním <xref:System.ServiceModel.Description.IMetadataExchange> konfigurace koncového bodu klienta. Nástroje Svcutil.exe automaticky načte z konfiguračního souboru <xref:System.ServiceModel.Description.IMetadataExchange> konfigurace koncového bodu klienta, který má stejný název jako schéma identifikátoru URI pro adresa koncového bodu metadat.  
  
## <a name="security"></a>Zabezpečení  
 Při publikování metadat prostřednictvím vlastní vazby, ujistěte se, že vazba poskytuje podpory zabezpečení, která vyžaduje metadata. Například k zabránili odhalení informací a zajistit vašeho klienta má právo získat metadata, můžete využít metadata a aplikace bezpečnější nakonfigurováním vaší <xref:System.ServiceModel.Description.IMetadataExchange> koncový bod pro vyžádání ověření a šifrování. Ukázka [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) ukazuje tento scénář.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení služeb](../../../../docs/framework/wcf/securing-services.md)  
 [Vazby WS-MetadataExchange](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)  
 [Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [Postupy: Načítání metadat přes vazbu jiného typu než MEX](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
