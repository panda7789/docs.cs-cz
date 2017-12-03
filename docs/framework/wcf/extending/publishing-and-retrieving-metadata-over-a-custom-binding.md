---
title: "Publikování a načítání metadat prostřednictvím vlastní vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f66821f38e8915ee93cf5b1b77dd75e32662121
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Publikování a načítání metadat prostřednictvím vlastní vazby
<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Poskytuje podporu pro přidání koncový bod metadat do služby. Tyto koncové body metadat může reagovat na požadavky HTTP GET na adresu URL, která má `?wsdl` řetězce dotazu a požadavky metody GET přenosu WS definovaným ve specifikaci WS-MetadataExchange (MEX). Koncové body MEX implementovat <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> kontrakt.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Publikování metadat prostřednictvím vlastní vazby  
 Koncové body metadat metody GET protokolu HTTP a HTTPS získat koncové body metadat jsou povoleny nastavením <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> vlastnosti, které chcete `true`. Nelze nakonfigurovat vazby u těchto koncových bodů.  
  
 <xref:System.ServiceModel.Description.IMetadataExchange> Kontrakt, ale dá použít s žádný koncový bod, včetně těch, které používají vlastní vazby, protože <xref:System.ServiceModel.Description.IMetadataExchange> koncové body jsou stejné jako libovolný jiný [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] koncový bod služby. Pokud víte, jak změnit konfiguraci vazby poskytované systémem, nebo pokud víte, jak nakonfigurovat <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, pak můžete nakonfigurovat vazby pro použití s <xref:System.ServiceModel.Description.IMetadataExchange> koncový bod.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Načítání metadat prostřednictvím vlastní vazby  
 Nejde načíst metadata z Get protokolu HTTP a HTTPS získat metadata koncové body pomocí standardní požadavků protokolu HTTP nebo HTTPS získat.  
  
 Pro načtení metadat z koncového bodu metadat MEX obecně můžete jedna z vazeb standardní MEX nepodporuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Typ a nástroje Svcutil.exe automaticky vyberte jednu z těchto standardní MEX vazeb na základě adresy Zadaná metadata koncového bodu.  
  
 Pokud koncový bod metadat MEX používá jinou vazbou než jedna z vazeb standardní MEX, můžete nakonfigurovat vazby používané <xref:System.ServiceModel.Description.MetadataExchangeClient> pomocí kódu nebo pomocí zadáním <xref:System.ServiceModel.Description.IMetadataExchange> konfigurace koncového bodu klienta. Nástroje Svcutil.exe automaticky načte z konfiguračního souboru <xref:System.ServiceModel.Description.IMetadataExchange> konfigurace koncového bodu klienta, který má stejný název jako schéma identifikátoru URI pro adresa koncového bodu metadat.  
  
## <a name="security"></a>Zabezpečení  
 Při publikování metadat prostřednictvím vlastní vazby, ujistěte se, že vazba poskytuje podpory zabezpečení, která vyžaduje metadata. Například k zabránili odhalení informací a zajistit vašeho klienta má právo získat metadata, můžete využít metadata a aplikace bezpečnější nakonfigurováním vaší <xref:System.ServiceModel.Description.IMetadataExchange> koncový bod pro vyžádání ověření a šifrování. Ukázka [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) ukazuje tento scénář.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení služeb](../../../../docs/framework/wcf/securing-services.md)  
 [Vazby WS-MetadataExchange](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)  
 [Postupy: Konfigurace vlastních metadat WS Exchange vazby](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [Postupy: načítání metadat přes vazbu jiného typu-MEX](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
