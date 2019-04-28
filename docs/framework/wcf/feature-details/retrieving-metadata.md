---
title: Načítání metadat
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], retrieving
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
ms.openlocfilehash: bb415d88c2bae75cb16aa137bdf867eb463afa63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748301"
---
# <a name="retrieving-metadata"></a>Načítání metadat
Načtení metadat je proces vyžádání a načítání metadat z koncových bodů metadat, jako je například metadata koncový bod WS-MetadataExchange (MEX) nebo koncový bod metadat HTTP/GET.  
  
## <a name="retrieving-metadata-from-the-command-line-using-svcutilexe"></a>Načítání metadat z příkazového řádku pomocí Svcutil.exe  
 Můžete načíst metadata služby WS-MetadataExchange nebo HTTP/GET požadavků pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj a předávání `/target:metadata` přepínače a adresu. Svcutil.exe metadat na zadané adrese stáhne a uloží soubor na disk. Pomocí svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance interně a načte z konfigurace <xref:System.ServiceModel.Description.IMetadataExchange> konfigurace koncového bodu, jejichž název odpovídá schématu adresy předán Svcutil.exe jako vstup.  
  
## <a name="retrieving-metadata-programmatically-using-the-metadataexchangeclient"></a>Načítání metadat prostřednictvím kódu programu pomocí Třída MetadataExchangeClient  
 Windows Communication Foundation (WCF) můžete načíst metadata služby pomocí standardizovaných protokolů, jako je WS-MetadataExchange a požadavky HTTP/GET. Obě tyto protokoly jsou podporovány <xref:System.ServiceModel.Description.MetadataExchangeClient> typu. Načtení služby metadata pomocí <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> typu poskytnutím adresu pro koncový bod metadat a volitelné vazby. Vazba používá <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance může být jedna z výchozích vazeb z <xref:System.ServiceModel.Description.MetadataExchangeBindings> statické třídy, vazbu uživatelem zadané nebo vazbu načíst z konfigurace koncového bodu pro `IMetadataExchange` kontraktu. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Můžete také vyřešit odkazy URL protokolu HTTP pomocí metadat <xref:System.Net.HttpWebRequest> typu.  
  
 Ve výchozím nastavení <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance je vázán na jediné <xref:System.ServiceModel.ChannelFactory> instance. Můžete změnit nebo nahradit <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> instanci použitou <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> tak, že přepíšete <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> virtuální metody. Podobně můžete změnit nebo nahradit <xref:System.Net.HttpWebRequest> instanci použitou <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> provádět požadavky HTTP/GET tak, že přepíšete <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> virtuální metody.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Stažení dokumentů metadat pomocí Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Popisuje způsob použití Svcutil.exe stažení dokumentů metadat.  
  
 [Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 Popisuje způsob použití <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> získání metadat vazby dynamicky za běhu.  
  
 [Postupy: Načítání metadat pomocí vlastnosti MetadataExchangeClient](../../../../docs/framework/wcf/feature-details/how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 Popisuje způsob použití <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> třídy ke stahování souborů metadat do <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> objekt, který obsahuje <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> objekty pro zápis do souborů nebo pro jiné účely.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.MetadataExchangeClient>
