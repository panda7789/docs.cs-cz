---
title: Publikování a načítání metadat prostřednictvím vlastní vazby
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 329daa39a14ed4c839ecbaa6cf9df036ceabee34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795512"
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Publikování a načítání metadat prostřednictvím vlastní vazby
<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Poskytuje podporu pro přidání koncového bodu metadat ke službě. Tyto koncové body metadat mohou reagovat na požadavky HTTP GET na adrese URL, které `?wsdl` mají QueryString a požadavky GET na WS-Transfer, jak jsou definovány ve specifikaci WS-MetadataExchange (MEX). Koncové body MEX implementují <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> kontrakt.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Publikování metadat přes vlastní vazbu  
 Koncové body metadat HTTP GET a HTTPS GET metadat jsou povoleny nastavením <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> vlastností nebo <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> na `true`. Vazby pro tyto koncové body nelze konfigurovat.  
  
 Kontrakt se ale dá použít s jakýmkoli koncovým bodem, včetně těch, které používají vlastní vazby, protože <xref:System.ServiceModel.Description.IMetadataExchange> koncové body jsou identické s jakýmkoli jiným koncovým bodem služby Windows Communication Foundation (WCF). <xref:System.ServiceModel.Description.IMetadataExchange> Pokud víte, jak upravit konfiguraci vazby poskytnuté systémem, nebo víte <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, jak nakonfigurovat, můžete nakonfigurovat vazbu pro použití <xref:System.ServiceModel.Description.IMetadataExchange> s koncovým bodem.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Načítání metadat prostřednictvím vlastní vazby  
 Metadata lze načíst z koncových bodů metadat HTTP GET a HTTPS GET pomocí standardních požadavků GET HTTP nebo HTTPS.  
  
 Pokud chcete načíst metadata z koncového bodu metadat MEX, můžete obecně použít jednu ze standardních vazeb MEX podporovaných službou WCF. Další informace naleznete v tématu <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Typ a nástroj Svcutil. exe automaticky vybere jednu z těchto standardních vazeb MEX založenou na adrese zadaného koncového bodu metadat.  
  
 Pokud koncový bod metadat MEX používá jinou vazbu než jednu ze standardních vazeb MEX, můžete nakonfigurovat vazbu používanou <xref:System.ServiceModel.Description.MetadataExchangeClient> pomocí kódu nebo <xref:System.ServiceModel.Description.IMetadataExchange> poskytnutím konfigurace koncového bodu klienta. Nástroj Svcutil. exe automaticky načte z konfiguračního souboru <xref:System.ServiceModel.Description.IMetadataExchange> konfiguraci koncového bodu klienta, která má stejný název jako schéma identifikátoru URI pro adresu koncového bodu metadat.  
  
## <a name="security"></a>Zabezpečení  
 Když publikujete metadata přes vlastní vazbu, zajistěte, aby vazba poskytovala podporu zabezpečení, kterou vaše metadata vyžaduje. Pokud například chcete zabránit vyzrazení informací a zajistit, aby měl váš klient právo získat metadata, můžete svá metadata a aplikace lépe zabezpečit tím, že nakonfigurujete <xref:System.ServiceModel.Description.IMetadataExchange> koncový bod tak, aby vyžadoval ověřování a šifrování. Tento scénář ukazuje ukázkový [Vlastní zabezpečený koncový bod metadat](../samples/custom-secure-metadata-endpoint.md) .  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení služeb](../securing-services.md)
- [Vazby WS-MetadataExchange](ws-metadataexchange-bindings.md)
- [Postupy: Konfigurace vlastní vazby WS-Metadata Exchange](how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [Postupy: Načtení metadat přes vazbu, která není MEX](how-to-retrieve-metadata-over-a-non-mex-binding.md)
