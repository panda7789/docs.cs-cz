---
title: Cloudy PNRP
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: 6e7ec5d88e1053f33b86816fec739aae38cac18c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623033"
---
# <a name="pnrp-clouds"></a>Cloudy PNRP
Protokol PNRP "cloud" představuje sadu uzlů, které mohou vzájemně komunikovat přes síť. Termín "cloud" je synonymem "partnerské sítě" a "peer-to-peer graf".  
  
 Komunikace mezi uzly by nikdy napříč z jednoho cloudu do jiného. A <xref:System.Net.PeerToPeer.Cloud> instance je jedinečně identifikovaný jeho název, který je velká a malá písmena. Jediné sdílené nebo uzel může být připojen k více než jeden cloud.  
  
 Cloudy jsou úzce vázané na síťová rozhraní.  Na počítači s více adresami se dvěma síťovými kartami, které jsou připojené k různým podsítím, bude vrácen tři cloudů: jeden pro každou z místní adresy odkaz na rozhraní a jeden globální obor cloudu.  
  
 Protokol PNRP používá tři cloud "oborů", ve kterých je obor seskupení počítačů, které jsou vzájemně najít:  
  
- Globální cloudové odpovídá globální rozsah adres protokolu IPv6 a globální adresy a představuje všechny počítače v celé Internet s protokolem IPv6. Existuje pouze jedna globální Cloudová.  
  
- Specifická pro připojení cloudových odpovídá rozsah adres protokolu IPv6 specifická pro připojení a adresy specifická pro připojení. Specifická pro připojení cloudu je pro konkrétní odkaz, který je obvykle stejné jako místně připojené podsítě. Může existovat více cloudů specifická pro připojení.  
  
 Třetí cloud, pro danou lokalitu cloudu odpovídá rozsah adres IPv6 serveru a místní adresy. Tento cloud je zastaralá, i když je stále podporovaná v PNRP.  
  
## <a name="clouds"></a>Cloudy  
 Cloudy PNRP jsou reprezentovány instance <xref:System.Net.PeerToPeer.Cloud> třídy. Skupiny cloudů použili partnerské zařízení jsou reprezentovány výskyty Výčtový typ <xref:System.Net.PeerToPeer.CloudCollection> třídy. Kolekce cloudy PNRP označuje aktuální peer lze získat voláním statické <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> metody.  
  
 Jednotlivé cloudy mít jedinečné názvy, reprezentovaný jako řetězec 256 znaků Unicode. Tyto názvy, spolu s výše uvedené oboru se používají k vytvoření jedinečné instancí třídy cloudu. Tyto instance lze serializovat a znovu vytvořena pro trvalé používání.  
  
 Po vytvoření nebo získat instance cloudové názvy partnerských uzlů můžete zaregistrovat ho k vytvoření sítě známého partnerským uzlům.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.PeerToPeer.Cloud>
- [Protokol PNRP](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
