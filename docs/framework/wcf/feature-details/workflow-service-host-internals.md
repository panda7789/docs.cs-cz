---
title: Interní informace o hostiteli služby pracovního postupu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 84bd0c5b93984e126019699caf64a61183c08f13
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="workflow-service-host-internals"></a>Interní informace o hostiteli služby pracovního postupu
<xref:System.ServiceModel.WorkflowServiceHost> poskytuje hostitele pro služby pracovních postupů. Zodpovídá za naslouchání pro příchozí zprávy a směrování je v instanci služby odpovídající pracovní postup, se řídí uvolnění a zachování nečinnosti pracovních postupů a další. Toto téma popisuje, jak hostitele služby pracovního postupu zpracovává příchozí zprávy.  
  
## <a name="workflowservicehost-overview"></a>Přehled hostitele služby pracovního postupu  
 <xref:System.ServiceModel.WorkflowServiceHost> Třída se používá k hostování služeb pracovních postupů. Ho poslouchá příchozí zprávy a směruje je do instance příslušné služby, vytvoření nové instance služby nebo načtení existující instance z odolná úložiště, podle potřeby.  Následující diagram znázorňuje na nejvyšší úrovni jak <xref:System.ServiceModel.WorkflowServiceHost> funguje.  
  
 ![Přehled hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/media/wfshhighlevel.gif "WFSHHighLevel")  
  
 Tento diagram ukazuje, že <xref:System.ServiceModel.WorkflowServiceHost> načte definice pracovního postupu služby z .xamlx souborů a načte informace o konfiguraci z konfiguračního souboru. Konfigurace sledování také načtenou z profilu sledování. <xref:System.ServiceModel.WorkflowServiceHost> zpřístupní koncový bod pracovního postupu ovládací prvek, který umožňuje odeslat operace ovládacího prvku do instance pracovního postupu.  Další informace najdete v části [kontrolní koncový bod pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) a [ukázka koncový bod pracovního postupu správy](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost> také poskytuje koncových bodů aplikace, které přijímat příchozí zprávy aplikace. Pokud dorazí příchozí zprávy odesláním v instanci služby příslušné pracovního postupu (Pokud je aktuálně načtený). V případě potřeby novou instanci pracovního postupu se vytvoří. Nebo pokud byla jako trvalé existující instance je načten z obchodu trvalost.  
  
## <a name="workflowservicehost-details"></a>Podrobnosti o hostitele služby pracovního postupu  
 Následující obrázek ukazuje, jak <xref:System.ServiceModel.WorkflowServiceHost> zpracovává zprávy trochu podrobněji.  
  
 ![Tok zpráv hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/media/wfshmessageflow.gif "WFSHMessageFlow")  
  
 Tento diagram zobrazuje tři různými koncovými body, koncový bod aplikace, ovládací prvek koncový bod pracovního postupu a hostování koncový bod pracovního postupu. Koncový bod aplikace přijímá zprávy, které nejsou pro instanci konkrétní pracovní postup. Kontrolní koncový bod pracovního postupu naslouchá operace ovládacího prvku. Pracovní postup, který je hostitelem koncového bodu přijímá zprávy, které způsobí <xref:System.ServiceModel.WorkflowServiceHost> načtení a provedení bez služby pracovních postupů. Jak je vidět v diagramu všechny zprávy jsou zpracovány WCF runtime.  Omezení instance pracovního postupu služby je dosaženo pomocí <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> vlastnost. Tato vlastnost omezí počet instancí služby souběžných pracovních postupů. Pokud toto omezení je překročena všechny další požadavky pro nové instance služby pracovního postupu nebo žádosti o aktivaci instancí trvalou pracovního postupu se zařadí do fronty. Požadavky ve frontě jsou zpracovány v pořadí FIFO bez ohledu na to, zda jsou požadavky na novou instanci nebo instance spuštěný, trvalý. Informace o zásadách hostitele je načtena, který určuje, jak jsou vyřešit neošetřené výjimky a nečinnosti pracovního postupu služby jsou uvolněna a trvalé. Další informace o těchto tématech naleznete v části [postupy: Konfigurace chování pracovního postupu neošetřené výjimky pomocí třídy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) a [postupy: Konfigurace chování nečinnosti pomocí WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md). Instance pracovního postupu se znovu načíst v případě potřeby a jsou nastavené jako trvalé podle zásad hostitele. Další informace o trvalost pracovního postupu v tématu: [postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md), a [trvalost pracovního postupu ](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 Následující obrázek znázorňuje, co se nazývá WorkflowServiceHost.Open.  
  
 ![Když je volána WorkflowServiceHost.Open](../../../../docs/framework/wcf/feature-details/media/wfhostopen.gif "WFHostOpen")  
  
 Pracovní postup je načtena z XAML a k vytvoření stromu aktivity. <xref:System.ServiceModel.WorkflowServiceHost> provede stromu aktivity a vytvoří popis služby. Konfigurace se použije na hostiteli. Nakonec hostitele začne naslouchat pro příchozí zprávy.  
  
 Následující obrázek znázorňuje, co <xref:System.ServiceModel.WorkflowServiceHost> nepodporuje, když obdrží zprávu vázaný aktivity Receive, který má CanCreateInstance nastavena na `true`.  
  
 ![Hostitel služby pracovního postupu přijme zprávu o](../../../../docs/framework/wcf/feature-details/media/wfhreceivemessagecci.gif "WFHReceiveMessageCCI")  
  
 Zpráva dorazí a zpracovává zásobníku kanálu WCF. Omezení jsou zaškrtnutá políčka a provedení korelace dotazy. Pokud zpráva je vázaný existující instance je zpráva doručena. Pokud je potřeba vytvořit novou instanci, zkontroluje se CanCreateInstance vlastnost Receive aktivity. Pokud je nastavena na hodnotu true, je vytvořena nová instance a doručí zprávy.  
  
 Následující obrázek znázorňuje, co <xref:System.ServiceModel.WorkflowServiceHost> nepodporuje, když obdrží zprávu vázaný aktivity Receive, který má CanCreateInstance nastaven na hodnotu false.  
  
 ![Hostitele služby pracovního postupu přijme zprávu o](../../../../docs/framework/wcf/feature-details/media/wfshreceivemessage.gif "WFSHReceiveMessage")  
  
 Zpráva dorazí a zpracovává zásobníku kanálu WCF. Omezení jsou zaškrtnutá políčka a provedení korelace dotazy. Zpráva je vázaný existující instance (protože CanCreateInstance je false) tak, aby instance je načtena z úložiště trvalosti, je obnovena záložku a spustí pracovní postup.  
  
> [!WARNING]
>  Hostitel služby pracovního postupu se nepodaří otevřít, i když systému SQL Server je nakonfigurován pro naslouchání pouze protokol pojmenovaný kanál.  
  
## <a name="see-also"></a>Viz také  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Hostování služeb pracovních postupů](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 [Kontrolní koncový bod pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 [Ukázka koncového bodu správy pracovního postupu](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md)  
 [Postupy: Konfigurace chování neošetřené výjimky pracovního postupu pomocí WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)  
 [Vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
 [Trvalost pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
