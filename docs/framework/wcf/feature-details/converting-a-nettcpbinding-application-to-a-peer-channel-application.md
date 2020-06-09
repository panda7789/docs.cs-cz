---
title: Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 42266d8c7c04e2d8f3f1e4734d9a05181c3f1ea3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595554"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Převedení aplikace NetTcpBinding na aplikaci rovnocenného kanálu
Propojení mezi klienty pomocí WinFX můžete vytvořit pomocí vazeb, které popisují parametry připojení. Převedení .NET Framework aplikace na použití připojení typu peer-to-peer vyžaduje vazbu, která tuto technologii podporuje při vytváření připojení klientů. Partnerský kanál poskytuje vazbu nazvanou <xref:System.ServiceModel.NetPeerTcpBinding> , kterou můžete použít podobným způsobem <xref:System.ServiceModel.NetTcpBinding> . Mezi klíčové rozdíly patří určení služby překladače a definování nastavení zabezpečení.  
  
 Pokud aplikace používá výchozí překladač a nastavení zabezpečení, převádění normální aplikace založené na klientech a serverech na použití rovnocenného kanálu zahrnuje změnu názvu vazby z "NetTcpBinding" na "NetPeerTcpBinding" v konfiguračním souboru aplikace. nemusíte tedy měnit základ kódu aplikace.  
  
## <a name="see-also"></a>Viz také

- [Vytvoření aplikace protokolu Peer Channel](building-a-peer-channel-application.md)
- [Vazby poskytované systémem](../system-provided-bindings.md)
