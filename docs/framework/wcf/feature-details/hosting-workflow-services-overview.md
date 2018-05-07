---
title: Přehled hostování služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: 7b5de31b5931af13b41b11af6e48a52b5628e27c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-workflow-services-overview"></a>Přehled hostování služeb pracovních postupů
K provedení musí být hostované služby pracovních postupů. <xref:System.ServiceModel.WorkflowServiceHost> Je hostitel pracovního postupu se na pole, která podporuje víc instancí, konfiguraci a zasílání zpráv WCF (i když nejsou vyžaduje použití zasílání zpráv aby bylo možné hostovat pracovních postupů).  Je integrován se sadou trvalost, sledování a řízení instance pomocí sady chování služby.  Stejně jako na WCF <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> můžete samoobslužně hostovaná v žádné spravované aplikace .NET nebo webové hostované (jako soubor .xamlx) ve službě IIS / byla.  Témata v této části popisují, jak k hostování služby pracovního postupu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Hostování služeb pracovních postupů](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 Popisuje hostování služeb pracovních postupů.  
  
 [Interní informace o hostiteli služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 Popisuje, jak <xref:System.ServiceModel.WorkflowServiceHost> zpracuje příchozí zprávy.  
  
 [Rozšiřitelnost hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 Popisuje, jak rozšířit funkce hostitele služby pracovního postupu.  
  
 [Kontrolní koncový bod pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 Popisuje, jak definovat koncový bod, který vám umožní vytvořit instance pracovního postupu.  
  
 [Postupy: Hostování pracovního postupu v IIS, který není součástí služby](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 Demonstruje hostování pracovní postup, který není služby pracovního postupu ve službě IIS.  
  
 [Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Ukazuje, jak k hostování služby pracovního postupu existující v systému Windows Server App Fabric.  
  
 [Konfigurace třídy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 Popisuje, jak řídit trvalost, sledování chování nečinnosti a neošetřené výjimky.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a>Související oddíly  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
