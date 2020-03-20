---
title: Cloudy PNRP
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: dd27e61fe1f648dcaf4ee4dd5f5119d33913c63a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047374"
---
# <a name="pnrp-clouds"></a>Cloudy PNRP
PNRP "cloud" představuje sadu uzlů, které mohou komunikovat mezi sebou prostřednictvím sítě. Termín "cloud" je synonymem pro "peer mesh" a "peer-to-peer graf".  
  
 Komunikace mezi uzly by nikdy neměla přecházet z jednoho cloudu do druhého. Instance <xref:System.Net.PeerToPeer.Cloud> je jednoznačně identifikována svým názvem, který rozlišuje malá a velká písmena. Jeden partner nebo uzel může být připojen k více než jednomu cloudu.  
  
 Mraky jsou velmi úzce spojeny se síťovými rozhraními.  V počítači s více adresami se dvěma síťovými kartami připojenými k různým podsítím budou vráceny tři cloudy: jedna pro každou místní adresu propojení na rozhraní a jeden cloud globálního oboru.  
  
 PNRP používá tři cloudové "obory", ve kterých je obor seskupením počítačů, které se vzájemně nacházejí:  
  
- Globální cloud odpovídá globálnímu oboru adres IPv6 a globálním adresám a představuje všechny počítače v celém Internetu IPv6. Existuje pouze jeden globální cloud.  
  
- Místní cloud propojení odpovídá oboru adresy IPv6 místního propojení a místním adresám propojení. Místní cloud propojení je pro konkrétní propojení, které je obvykle stejné jako místně připojené podsítě. Může existovat více místních cloudů propojení.  
  
 Třetí cloud, cloud specifický pro lokalitu, odpovídá oboru adresy IPv6 lokality a místním adresám lokality. Tento cloud byl zastaralé, i když je stále podporován v PNRP.  
  
## <a name="clouds"></a>Cloudy  
 PNRP mraky jsou reprezentovány <xref:System.Net.PeerToPeer.Cloud> instance mi. Skupiny cloudů používaných partnera jsou reprezentovány <xref:System.Net.PeerToPeer.CloudCollection> instancemi výčtu třídy. Kolekce PNRP mraků známých aktuálnímu partnerovi <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> lze získat voláním statické metody.  
  
 Jednotlivé mraky mají jedinečné názvy, reprezentované jako 256 znaků Unicode řetězec. Tyto názvy, spolu s výše uvedeným oboru, se používají k vytvoření jedinečné instance Cloud třídy. Tyto instance lze serializovat a rekonstruovat pro trvalé použití.  
  
 Jakmile je instance Cloud vytvořena nebo získána, mohou být u ní registrovány názvy rovnocenných počítačů a vytvořit síť známých partnerů.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.PeerToPeer.Cloud>
- [Protokol PNRP (Peer Name Resolution Protocol)](peer-name-resolution-protocol.md)
