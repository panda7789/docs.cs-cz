---
title: Přehled hostování služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: 10ea35fc1988e1b3e6ceb44aca098e63bfc7d7e4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597290"
---
# <a name="hosting-workflow-services-overview"></a>Přehled hostování služeb pracovních postupů
Aby bylo možné spustit službu pracovního postupu, je nutné ji hostovat. Je předem připravený <xref:System.ServiceModel.WorkflowServiceHost> hostitel pracovního postupu, který podporuje více instancí, konfigurací a zasílání zpráv WCF (i když pracovní postupy nevyžadují, aby používaly zasílání zpráv, aby bylo možné je hostovat).  Integruje se taky se zachováním, sledováním a instancí prostřednictvím sady chování služby.  Stejně jako v případě WCF se může v rámci <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.WorkflowServiceHost> služby IIS/was hostovat v jakékoli spravované aplikaci .NET nebo v hostovaném webovém prostředí (jako soubor. xamlx).  Témata v této části popisují, jak hostovat službu pracovního postupu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Hostování služeb pracovních postupů](hosting-workflow-services.md)  
 Popisuje služby hostování pracovního postupu.  
  
 [Interní informace o hostiteli služby pracovního postupu](workflow-service-host-internals.md)  
 Popisuje způsob <xref:System.ServiceModel.WorkflowServiceHost> zpracování příchozích zpráv.  
  
 [Rozšiřitelnost hostitele služby pracovního postupu](workflow-service-host-extensibility.md)  
 V této části najdete popis postupu rozšiřování funkcí hostitele služby pracovního postupu.  
  
 [Kontrolní koncový bod pracovního postupu](workflow-control-endpoint.md)  
 Popisuje, jak definovat koncový bod, který umožňuje vytvářet instance pracovního postupu.
  
 [Postupy: Hostování služby pracovního procesu pomocí Windows Server App Fabric](how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Ukazuje, jak hostovat existující službu pracovního postupu ve Windows Server App Fabric.  
  
 [Konfigurace třídy WorkflowServiceHost](configuring-workflowservicehost.md)  
 Popisuje, jak řídit chování při persistenci, sledování, nečinnosti a neošetřené výjimce.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a>Související oddíly  
 [Služby pracovních postupů](workflow-services.md)
