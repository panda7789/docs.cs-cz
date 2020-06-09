---
title: Řízení výkonu služby WCF pomocí třídy ServiceThrottlingBehavior
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: 9cc5141805504bc46391105f475860b032f12d32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600228"
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a>Řízení výkonu služby WCF pomocí třídy ServiceThrottlingBehavior
<xref:System.ServiceModel.Description.ServiceThrottlingBehavior>Třída zveřejňuje vlastnosti, které lze použít k omezení počtu instancí nebo relací, které jsou vytvořeny na úrovni aplikace. Pomocí tohoto chování můžete vyladit výkon aplikace Windows Communication Foundation (WCF).  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>Řízení instancí služby a souběžných volání  
 Vlastnost slouží <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> k určení maximálního počtu zpráv, které jsou aktivně zpracovávány v rámci <xref:System.ServiceModel.ServiceHost> třídy, a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> vlastnosti pro určení maximálního počtu <xref:System.ServiceModel.InstanceContext> objektů ve službě.  
  
 Vzhledem k tomu, že určení nastavení těchto vlastností obvykle probíhá po reálných zkušenostech, které spouští aplikaci proti zatížení, jsou nastavení <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> vlastností obvykle specifikována v konfiguračním souboru aplikace pomocí [\<serviceThrottling>](../../configure-apps/file-schema/wcf/servicethrottling.md) elementu.  
  
 Následující příklad kódu ukazuje použití <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> třídy z konfiguračního souboru aplikace, který nastaví <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> vlastnosti, a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> jako triviální příklad vlastností na 1. Reálné prostředí určuje optimální nastavení pro konkrétní aplikaci.  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 Přesné chování za běhu závisí na hodnotách <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastností a, které určují, kolik zpráv lze provádět v rámci operace najednou, a životnost služby <xref:System.ServiceModel.InstanceContext> vzhledem k relacím příchozích kanálů v uvedeném pořadí.  
  
 Podrobnosti najdete v tématech <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> .  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
