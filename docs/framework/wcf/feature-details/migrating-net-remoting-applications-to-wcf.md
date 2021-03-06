---
title: Migrace aplikací vzdálené komunikace .NET do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: d12583904e4a025a8de1103f0fb48f4656d6855e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598772"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrace aplikací vzdálené komunikace .NET do WCF
**Toto téma je specifické pro starší verze technologie, která se zachovává kvůli zpětné kompatibilitě se stávajícími aplikacemi a nedoporučuje se pro nový vývoj. Distribuované aplikace by se teď měly vyvíjet pomocí WCF.**  
  
 Existují dva způsoby, jak využít WCF se stávajícími aplikacemi vzdálené komunikace .NET: integrace a migrace. Integrace umožňuje, aby se Vzdálená komunikace .NET 2,0 a WCF běžely souběžně, což vám umožní vystavit stejné obchodní objekty i přes obě technologie, aniž by bylo nutné měnit stávající kód vzdálené 2,0 komunikace v rozhraní .NET. Integrace vyžaduje, abyste spustili .NET Framework 2,0 nebo vyšší. Pokud chcete využít výhod funkcí WCF a nepotřebujete kompatibilitu s komunikací se systémy vzdálené komunikace 2,0, můžete migrovat celou službu na WCF. Migrace z technologie vzdálené komunikace .NET 2,0 na WCF vyžaduje změny rozhraní vzdáleného objektu a jeho nastavení konfigurace. Obě tato témata jsou popsaná v tématu [Vzdálená komunikace s Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80)).  
  
## <a name="see-also"></a>Viz také

- [Koncepční přehled](../conceptual-overview.md)
