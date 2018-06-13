---
title: Migrace aplikací vzdálené komunikace .NET do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 53f63352503a48ee849580e676b5fe98f3dcf2cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492493"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrace aplikací vzdálené komunikace .NET do WCF
**Toto téma je specifické pro starší verze technologie, která se zachovává kvůli zpětné kompatibilitě se stávajícími aplikacemi a nedoporučuje se používat pro vývoj. Distribuované aplikace by měla být nyní vyvinuté pomocí WCF.**  
  
 Existují dva způsoby, jak využít výhod WCF se stávajícími aplikacemi .NET Remoting: integrace a migrace. Integrace umožňuje, abyste měli .net Remoting 2.0 a WCF s kódem na straně stranou, umožňuje vystavit stejné objekty obchodní přes obě technologie současně, bez nutnosti upravovat vaše stávající rozhraní .net 2.0 vzdálenou komunikaci. Integrace vyžaduje, že používáte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 nebo vyšší. Pokud chcete využít výhod funkce WCF a není nutné přenosová kompatibilitu s systémy 2.0 vzdálenou komunikaci, můžete migrovat celou službou WCF. Migrace z .NET Remoting 2.0 do WCF vyžaduje změny ke vzdálenému objektu rozhraní a jeho nastavení konfigurace. Obě tato témata jsou popsané v [ze vzdálené komunikace do služby Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Viz také  
 [Koncepční přehled](../../../../docs/framework/wcf/conceptual-overview.md)
