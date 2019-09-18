---
title: Cloudy PNRP
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: dd27e61fe1f648dcaf4ee4dd5f5119d33913c63a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047374"
---
# <a name="pnrp-clouds"></a>Cloudy PNRP
Cloud PNRP "Cloud" představuje sadu uzlů, které mohou vzájemně komunikovat přes síť. Pojem "Cloud" je synonymum s "rovnocennými oky" a "graf peer-to-peer".  
  
 Komunikace mezi uzly by nikdy neměla překročit jeden Cloud do jiného. <xref:System.Net.PeerToPeer.Cloud> Instance je jednoznačně identifikována podle názvu, což rozlišuje velká a malá písmena. Jeden partner nebo uzel je možné připojit k více než jednomu cloudu.  
  
 Cloudy jsou velmi pečlivě vázané na síťová rozhraní.  U více domácích počítačů se dvěma síťovými kartami připojenými k různým podsítím budou vráceny tři cloudy: jeden pro každý z místních adres propojení na rozhraní a jeden Cloud globálního oboru.  
  
 Protokol PNRP používá tři cloudové obory, ve kterých je obor seskupením počítačů, které je možné navzájem najít:  
  
- Globální Cloud odpovídá globálnímu oboru IPv6 adres a globálním adresám a představuje všechny počítače v celé síti Internet s protokolem IPv6. Existuje pouze jeden globální Cloud.  
  
- Místní cloudový odkaz odpovídá rozsahu adres IPv6 místních odkazů a adresám místní připojení. Místní cloudový odkaz je pro konkrétní odkaz, který je obvykle stejný jako připojená podsíť místně. Může existovat několik cloudových místních propojení.  
  
 Třetí Cloud, který je specifický pro konkrétní lokalitu, odpovídá rozsahu IPv6 adres lokality a místním adresám lokality. Tento Cloud je zastaralý, i když je stále podporovaný v PNRP.  
  
## <a name="clouds"></a>Cloud  
 Cloudy PNRP jsou reprezentovány instancemi <xref:System.Net.PeerToPeer.Cloud> třídy. Skupiny cloudů používajících partnera jsou zastoupeny instancemi vyčíslitelné <xref:System.Net.PeerToPeer.CloudCollection> třídy. Kolekce cloudů PNRP známých pro aktuálního partnera může být získána voláním statické <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> metody.  
  
 Jednotlivé cloudy mají jedinečné názvy reprezentované jako řetězec znakové sady Unicode 256. Tyto názvy společně s výše uvedeným oborem slouží k vytváření jedinečných instancí třídy cloudu. Tyto instance lze serializovat a znovu sestavit pro trvalé použití.  
  
 Jakmile se vytvoří nebo získá instance cloudu, můžete s ní zaregistrovat rovnocenné názvy, aby bylo možné vytvořit síť se známými partnerskými uzly.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.PeerToPeer.Cloud>
- [Protokol PNRP](peer-name-resolution-protocol.md)
