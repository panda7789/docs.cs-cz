---
title: Přehled hostování služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: dbe271e30e9c4e98a52c01ffaa21de25c127c7ff
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208427"
---
# <a name="hosting-workflow-services-overview"></a>Přehled hostování služeb pracovních postupů
Ke spuštění musí být hostovaný služeb pracovních postupů. <xref:System.ServiceModel.WorkflowServiceHost> Je hostitele pracovního postupu out-of-the-box, která podporuje víc instancí, konfiguraci a zasílání zpráv WCF (i když nejsou potřeba použít zasílání aby bylo možné hostovat pracovních postupů).  Je integrován se sadou trvalost, sledování a řízení instance prostřednictvím sady chování služby.  Stejně jako jeho WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> můžete ve všech spravovaných aplikací .NET v místním prostředí nebo web hostované (jako soubor .xamlx) ve službě IIS nebo WAS.  Témata v této části popisují, jak k hostování služby pracovního postupu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Hostování služeb pracovních postupů](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 Popisuje hostování služeb pracovních postupů.  
  
 [Interní informace o hostiteli služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 Popisuje, jak <xref:System.ServiceModel.WorkflowServiceHost> zpracovává příchozí zprávy.  
  
 [Rozšiřitelnost hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 Popisuje, jak rozšířit funkce hostitele služby pracovního postupu.  
  
 [Kontrolní koncový bod pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 Popisuje, jak definovat koncový bod, který vám umožní vytvořit instance pracovního postupu.
  
 [Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Ukazuje, jak hostovat existující služby pracovního postupu v systému Windows Server App Fabric.  
  
 [Konfigurace třídy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 Popisuje, jak řídit trvalost, sledování, nečinnosti a neošetřené výjimky chování.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a>Související oddíly  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
