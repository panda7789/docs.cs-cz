---
title: Migrace aplikací vzdálené komunikace .NET do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: c0ce7c9badc8bad6eedc58827b6efe2595ab2cf8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592863"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrace aplikací vzdálené komunikace .NET do WCF
**Toto téma se věnuje starší technologie, která se zachovává kvůli zpětné kompatibilitě se stávajícími aplikacemi a nedoporučuje se používat pro vývoj nových projektů. Distribuované aplikace by měla nyní být vyvinuto s použitím WCF.**  
  
 Existují dva způsoby, jak využít výhod WCF se stávajícími aplikacemi .NET Remoting: integrace a migrace. Integrace umožňuje mít 2.0 vzdálené komunikace .NET a WCF souběžné spuštění, umožňuje vystavit stejné objekty obchodní přes obou technologií současně, aniž byste museli změnit váš stávající kód 2.0 vzdálené komunikace .NET. Integrace vyžaduje také, že používáte v rozhraní .NET Framework 2.0 nebo vyšší. Pokud chcete využít výhod funkcí WCF a není nutné kompatibility při přenosu pomocí vzdálené komunikace 2.0 systémů, můžete migrovat celou službu do WCF. Migrace z verze 2.0 vzdálené komunikace .NET na WCF vyžaduje změny v rozhraní vzdáleného objektu a jeho nastavení konfigurace. Obě tato témata se věnují [ze vzdálené komunikace Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Viz také:

- [Koncepční přehled](../../../../docs/framework/wcf/conceptual-overview.md)
