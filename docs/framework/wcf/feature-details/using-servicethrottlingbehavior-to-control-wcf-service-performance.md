---
title: Řízení výkonu služby WCF pomocí třídy ServiceThrottlingBehavior
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: b54d1d6146b9751fdd12502771de01fe52854c07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a>Řízení výkonu služby WCF pomocí třídy ServiceThrottlingBehavior
<xref:System.ServiceModel.Description.ServiceThrottlingBehavior> Třída zpřístupní vlastnosti, které můžete použít k omezení, kolik instancí nebo relací jsou vytvořené na úrovni aplikace. Toto chování lze optimalizovat výkon aplikace Windows Communication Foundation (WCF).  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>Řízení instance služby a souběžných volání  
 Použití <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> vlastnosti a určit maximální počet zpráv aktivně zpracovávají napříč <xref:System.ServiceModel.ServiceHost> třída a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> vlastnosti a určit maximální počet <xref:System.ServiceModel.InstanceContext> objekty ve službě.  
  
 Protože určení nastavení pro tyto vlastnosti obvykle probíhá po spuštění aplikace proti praktických zkušeností načte, nastavení <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> vlastnosti se obvykle zadává v souboru konfigurace aplikace pomocí [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) element.  
  
 Následující příklad kódu ukazuje použití <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> třídy z konfiguračního souboru aplikace, který nastaví <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> vlastnosti na hodnotu 1 jako jednoduchý příklad. Reálného prostředí určuje optimální nastavení pro všechny konkrétní aplikace.  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 Přesný běhového chování závisí na hodnoty <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnosti, které řídí, kolik zpráv můžete provést uvnitř operace najednou a životnosti služby <xref:System.ServiceModel.InstanceContext> relativně k příchozích relací kanálu , v uvedeném pořadí.  
  
 Podrobnosti najdete v tématu <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, a <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
