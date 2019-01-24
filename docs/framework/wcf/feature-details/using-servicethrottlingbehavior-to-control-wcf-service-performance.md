---
title: Řízení výkonu služby WCF pomocí třídy ServiceThrottlingBehavior
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: 77fe2d3bb7f0e9c9d2e2defd4aa8c0053799406b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609496"
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a>Řízení výkonu služby WCF pomocí třídy ServiceThrottlingBehavior
<xref:System.ServiceModel.Description.ServiceThrottlingBehavior> Třída zveřejňuje vlastnosti, které vám umožní omezit počet instancí nebo relace se vytvářejí na úrovni aplikace. Toto chování lze optimalizovat výkon vaší aplikace Windows Communication Foundation (WCF).  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>Řízení instancí služby a souběžných volání  
 Použití <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> vlastnosti a určit maximální počet zpráv aktivně pracujících přes <xref:System.ServiceModel.ServiceHost> třídy a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> vlastnosti a určit maximální počet <xref:System.ServiceModel.InstanceContext> objekty ve službě.  
  
 Protože určující nastavení těchto vlastností, obvykle probíhá po skutečných praxe s provozem aplikací proti načtení nastavení <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> vlastnosti se obvykle zadává v souboru konfigurace aplikace pomocí [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) elementu.  
  
 Následující příklad kódu ukazuje použití <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> třídy z konfiguračního souboru aplikace, který nastaví <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> vlastnosti na hodnotu 1 jako příklad jednoduchého dotazu. Reálných zkušenostech určuje optimální nastavení pro každou konkrétní aplikaci.  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 Přesné chování za běhu, závisí na hodnoty <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnosti, které řídí, kolik zpráv lze spustit v operaci najednou a životnosti služby <xref:System.ServiceModel.InstanceContext> vzhledem k příchozích relací kanálu , v uvedeném pořadí.  
  
 Podrobnosti najdete v tématu <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
