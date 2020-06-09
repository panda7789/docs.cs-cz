---
title: Načítání metadat
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], retrieving
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
ms.openlocfilehash: 5488e2b0778738927922edab0f948645b816a1f6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586218"
---
# <a name="retrieving-metadata"></a>Načítání metadat
Načtení metadat je proces vyžádání a načtení metadat z koncového bodu metadat, jako je například koncový bod metadat WS-MetadataExchange (MEX) nebo koncový bod metadat HTTP/GET.  
  
## <a name="retrieving-metadata-from-the-command-line-using-svcutilexe"></a>Načítání metadat z příkazového řádku pomocí Svcutil. exe  
 Metadata služby můžete načíst pomocí požadavků WS-MetadataExchange nebo HTTP/GET pomocí nástroje Nástroj pro dodávání [metadat (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) a předáním `/target:metadata` přepínače a adresy. Svcutil. exe stáhne metadata na zadané adrese a uloží soubor na disk. Svcutil. exe <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> interně používá instanci a načítá z konfigurace <xref:System.ServiceModel.Description.IMetadataExchange> konfiguraci koncového bodu, jejíž název odpovídá schématu adresy předané do Svcutil. exe jako vstup.  
  
## <a name="retrieving-metadata-programmatically-using-the-metadataexchangeclient"></a>Načítají se metadata programově pomocí MetadataExchangeClient.  
 Windows Communication Foundation (WCF) může načítat metadata služby pomocí standardizovaných protokolů, jako jsou WS-MetadataExchange a požadavky HTTP/GET. Oba tyto protokoly jsou podporovány <xref:System.ServiceModel.Description.MetadataExchangeClient> typem. Metadata služby můžete načíst pomocí <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> typu poskytnutím adresy pro koncový bod metadat a volitelné vazby. Vazba, kterou používá <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance, může být jedna z výchozích vazeb ze <xref:System.ServiceModel.Description.MetadataExchangeBindings> statické třídy, uživatelsky zadané vazby nebo vazby načtené z konfigurace koncového bodu pro `IMetadataExchange` kontrakt. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>Může také vyřešit odkazy adresy URL http na metadata pomocí <xref:System.Net.HttpWebRequest> typu.  
  
 Ve výchozím nastavení <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> je instance svázána s jednou <xref:System.ServiceModel.ChannelFactory> instancí. Můžete změnit nebo nahradit instanci, kterou <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> používá, <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> přepsáním <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> virtuální metody. Podobně můžete změnit nebo nahradit instanci, kterou <xref:System.Net.HttpWebRequest> používá, <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> k provádění požadavků HTTP/GET přepsáním <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> virtuální metody.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe](how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Ukazuje, jak používat Svcutil. exe ke stažení dokumentů metadat.  
  
 [Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 Ukazuje, jak použít, <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> Chcete-li dynamicky získat metadata vazby za běhu.  
  
 [Postupy: Načítání metadat pomocí vlastnosti MetadataExchangeClient](how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 Ukazuje, jak použít <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> třídu ke stažení souborů metadat do <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> objektu, který obsahuje <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> objekty pro zápis do souborů nebo pro jiné účely.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Description.MetadataExchangeClient>
