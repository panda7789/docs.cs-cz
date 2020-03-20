---
title: Interní informace o hostiteli služby pracovního postupu
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: b95a59b0e1715b3cc18ccfea44d6c4ccd04ca5ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184166"
---
# <a name="workflow-service-host-internals"></a>Interní informace o hostiteli služby pracovního postupu
<xref:System.ServiceModel.WorkflowServiceHost>poskytuje hostitele pro služby pracovního postupu. Je zodpovědný za naslouchání příchozích zpráv a směrování je do příslušné instance služby pracovního postupu, řídí uvolnění a uchování nečinnosti pracovních postupů a další. Toto téma popisuje, jak WorkflowServiceHost zpracovává příchozí zprávy.  
  
## <a name="workflowservicehost-overview"></a>WorkflowServiceHost – přehled  

Třída <xref:System.ServiceModel.WorkflowServiceHost> se používá k hostování služeb pracovního postupu. Naslouchá příchozízprávy a směruje je do příslušné instance služby, vytváření nových instancí nebo načítání existujících instancí z trvalého úložiště podle potřeby. Následující diagram znázorňuje na <xref:System.ServiceModel.WorkflowServiceHost> vysoké úrovni, jak funguje:
  
 ![Diagram, který znázorňuje přehled hostitele služby pracovního postupu.](./media/workflow-service-host-internals/workflow-service-host-high-level-overview.gif)  
  
 Tento diagram <xref:System.ServiceModel.WorkflowServiceHost> ukazuje, že načte definice služeb pracovního postupu ze souborů .xamlx a načte informace o konfiguraci z konfiguračního souboru. Také načte konfiguraci sledování z profilu sledování. <xref:System.ServiceModel.WorkflowServiceHost>zpřístupňuje koncový bod ovládacího prvku pracovního postupu, který umožňuje odesílat operace ovládacího prvku do instancí pracovního postupu.  Další informace naleznete [v tématu Ukázka koncového bodu ovládacího prvku pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost>také zpřístupňuje koncové body aplikace, které naslouchá příchozí zprávy aplikace. Když přijde příchozí zpráva, je odeslána do příslušné instance služby pracovního postupu (pokud je aktuálně načtena). V případě potřeby je vytvořena nová instance pracovního postupu. Nebo pokud existující instance byla trvalá, je načtena z úložiště trvalosti.  
  
## <a name="workflowservicehost-details"></a>Podrobnosti pracovního postupu ServiceHost  
 Následující diagram znázorňuje, jak <xref:System.ServiceModel.WorkflowServiceHost> zpracovává zprávy v trochu podrobněji:  
  
 ![Diagram, který zobrazuje tok zpráv hostitele služby pracovního postupu.](./media/workflow-service-host-internals/workflow-service-host-message-flow.gif)  
  
 Tento diagram znázorňuje tři různé koncové body, koncový bod aplikace, koncový bod řízení pracovního postupu a koncový bod hostování pracovního postupu. Koncový bod aplikace přijímá zprávy, které jsou vázány na konkrétní instanci pracovního postupu. Koncový bod ovládacího prvku pracovního postupu naslouchá operacím ovládacího prvku. Koncový bod hostování pracovního postupu <xref:System.ServiceModel.WorkflowServiceHost> naslouchá zprávám, které způsobují načtení a spuštění pracovních postupů, které nejsou službami. Jak je znázorněno na obrázku všechny zprávy jsou zpracovány prostřednictvím za běhu WCF.  Omezení instance služby pracovního postupu <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> je dosaženo pomocí vlastnosti. Tato vlastnost omezí počet souběžných instancí služby pracovního postupu. Při překročení tohoto omezení budou všechny další požadavky na nové instance služby pracovního postupu nebo požadavky na aktivaci trvalých instancí pracovního postupu zařazeny do fronty. Požadavky ve frontě jsou zpracovány v pořadí FIFO bez ohledu na to, zda se jedná o požadavky na novou instanci nebo spuštěnou, trvalou instanci. Jsou načteny informace o zásadách hostitele, které určují, jak jsou zpracovány neošetřené výjimky a jak jsou uvolněny a trvalé služby pracovního postupu nečinnosti. Další informace o těchto tématech naleznete v [tématu How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) and [How to: Configure Idle Behavior with WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md). Instance pracovního postupu jsou trvalé podle zásad hostitele a v případě potřeby se znovu načítají. Další informace o trvalost pracovního postupu naleznete v [tématu: Postup: Konfigurace trvalosti pomocí služby WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [Vytvoření dlouhotrvající služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)a [Trvalosti pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 Následující obrázek znázorňuje tok při volání WorkflowServiceHost.Open:  
  
 ![Diagram, který ukazuje tok při WorkflowServiceHost.Open je volána.](./media/workflow-service-host-internals/workflow-service-host-open.gif)  
  
 Pracovní postup je načten z XAML a vytvoří se strom aktivit. <xref:System.ServiceModel.WorkflowServiceHost>prochází stromem aktivit a vytvoří popis služby. Konfigurace je použita pro hostitele. Nakonec hostitel začne naslouchat příchozízprávy.  
  
 Následující obrázek znázorňuje, co <xref:System.ServiceModel.WorkflowServiceHost> dělá, když obdrží zprávu vázanou na `true`příjem aktivity, která má CanCreateInstance nastavena na :  
  
 ![Rozhodovací strom používaný hostitelem WFS, když obdrží zprávu a CanCreateInstance je true.](./media/workflow-service-host-internals/workflow-service-host-receive-message-cancreateinstance.gif)  
  
 Zpráva dorazí a je zpracována zásobníku kanálu WCF. Škrticí klapky jsou kontrolovány a korelace dotazy jsou spouštěny. Pokud je zpráva vázána na existující instanci, je zpráva doručena. Pokud je potřeba vytvořit novou instanci, je zaškrtnuta vlastnost CanCreateInstance aktivity příjmu. Pokud je nastavena na hodnotu true, je vytvořena nová instance a zpráva je doručena.  
  
 Následující obrázek znázorňuje, co <xref:System.ServiceModel.WorkflowServiceHost> dělá, když obdrží zprávu vázanou na příjem aktivity, která má CanCreateInstance nastavena na false.  
  
 ![Rozhodovací strom používaný hostitelem WFS, když obdrží zprávu a CanCreateInstance je false.](./media/workflow-service-host-internals/workflow-service-host-receive-message.gif)  
  
 Zpráva dorazí a je zpracována zásobníku kanálu WCF. Škrticí klapky jsou kontrolovány a korelace dotazy jsou spouštěny. Zpráva je vázána na existující instanci (protože CanCreateInstance je false), takže instance je načtena z úložiště trvalosti, záložka se obnoví a pracovní postup se spustí.  
  
> [!WARNING]
> Hostitel služby pracovního postupu se nepodaří otevřít, pokud je sql server nakonfigurován tak, aby naslouchal pouze protokolu NamedPipe.  
  
## <a name="see-also"></a>Viz také

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Hostování služeb pracovních postupů](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)
- [Kontrolní koncový bod pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)
- [Postupy: Konfigurace chování neošetřené výjimky pracovního postupu pomocí WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)
- [Vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [Trvalost pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
