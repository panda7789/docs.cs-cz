---
title: Cloudy PNRP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f142c7aaa71ab2dbee1d2955f2c235a65e6c8bfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="pnrp-clouds"></a>Cloudy PNRP
PNRP "cloud" představuje sadu uzlů, které lze vzájemně komunikovat přes síť. Termín "cloud" je totožná s "peer-to-peer graf" a "sdílené OK".  
  
 Komunikace mezi uzly by nikdy křížová z jednoho cloudu do jiného. A <xref:System.Net.PeerToPeer.Cloud> instance je jedinečně identifikovaný jeho název, který je malá a velká písmena. Jedinou druhou stranu nebo uzel může být připojen k více než jeden cloud.  
  
 Cloudy jsou velmi úzce svázané s síťových rozhraní.  Na počítači více adresami se dvěma síťovými kartami připojené k různým podsítím bude vrácen tři cloudů: jeden pro každou z místní adresy odkaz na rozhraní a jeden globální obor cloudu.  
  
 PNRP používá tři cloudu "obory", ve kterých je obor seskupení počítačů, které se nepodařilo najít vzájemně:  
  
-   Globální cloudu odpovídá globální rozsah IPv6 adres a globální adresy a představuje všechny počítače v celé Internet s protokolem IPv6. Není k dispozici pouze jeden globální cloud.  
  
-   Místní cloudu odpovídá místní rozsah adres protokolu IPv6 a místní adresy. Místní cloudu je pro konkrétní připojení, což je většinou stejný jako místně připojené podsítě. Může existovat více cloudů specifická pro připojení.  
  
 Třetí cloudu, jednotlivých lokalit cloudu, odpovídá rozsah adres IPv6 lokality a místní adresy. Tento cloud se už nepoužívá, i když se pořád podporuje v PNRP.  
  
## <a name="clouds"></a>Cloudy  
 PNRP cloudy jsou reprezentované pomocí instance <xref:System.Net.PeerToPeer.Cloud> třídy. Skupiny cloudů používat sdílené jsou reprezentované pomocí instance Výčtový typ <xref:System.Net.PeerToPeer.CloudCollection> třídy. Je možné získat kolekce PNRP cloudů ví, že aktuální sdílené volání statických <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> metoda.  
  
 Jednotlivé cloudy mít jedinečné názvy, vyjádřené řetězec 256 znaků Unicode. Názvy těchto spolu s výše uvedené oboru, se používají k vytvoření jedinečné instancí třídy cloudu. Tato instance může serializovat a znovu vytvořena pro trvalé používání.  
  
 Po vytvoření nebo získat instanci cloudu, můžete se s ním vytvořit mřížku známé partnerské uzly zaregistrovat sdílené názvy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.PeerToPeer.Cloud>  
 [Protokol PNRP](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
