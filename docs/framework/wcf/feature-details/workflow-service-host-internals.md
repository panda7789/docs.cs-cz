---
title: Interní informace o hostiteli služby pracovního postupu
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: 0596e15e27460a08f859ec3398afbeae752c86fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826025"
---
# <a name="workflow-service-host-internals"></a>Interní informace o hostiteli služby pracovního postupu
<xref:System.ServiceModel.WorkflowServiceHost> poskytuje hostitele služby pracovního postupu. Je zodpovědná za naslouchání pro příchozí zprávy a směrování je instance služby příslušné pracovní postup, se řídí uvolnění a při zachování nečinných pracovních postupů a dalších. Toto téma popisuje, jak hostitele služby pracovního postupu zpracování příchozích zpráv.  
  
## <a name="workflowservicehost-overview"></a>Přehled třídy WorkflowServiceHost  

<xref:System.ServiceModel.WorkflowServiceHost> Třída se používá k hostování služeb pracovních postupů. Poslouchá příchozí zprávy a směruje je do příslušné službě instance, vytváření nových instancí nebo načítání existující instance z trvalého úložiště, podle potřeby. Následující diagram znázorňuje nejvyšší úrovni o <xref:System.ServiceModel.WorkflowServiceHost> funguje: 
  
 ![Diagram, který ukazuje přehled hostitele služby pracovního postupu.](./media/workflow-service-host-internals/workflow-service-host-high-level-overview.gif)  
  
 Tento diagram znázorňuje, že <xref:System.ServiceModel.WorkflowServiceHost> načte definice pracovního postupu služby ze souborů .xamlx a načte informace o konfiguraci z konfiguračního souboru. Konfigurace sledování se také načtou z profilu sledování. <xref:System.ServiceModel.WorkflowServiceHost> poskytuje ovládací prvek koncový bod pracovního postupu, který umožňuje odeslat operace u ovládacího prvku do instance pracovního postupu.  Další informace najdete v části [ukázkový pracovní postup kontrolní koncový bod](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost> také poskytuje aplikačními koncovými body, které naslouchání pro příchozí zprávy aplikace. Příchozí zpráva dorazí jsou odeslána do instance služby odpovídající pracovního postupu (Pokud je aktuálně načtená). V případě potřeby nové instance pracovního postupu je vytvořena. Nebo pokud byla trvale uložena existující instanci je načten z úložiště trvalosti.  
  
## <a name="workflowservicehost-details"></a>Podrobnosti hostitele služby pracovního postupu  
 Následující obrázek ukazuje, jak <xref:System.ServiceModel.WorkflowServiceHost> zpracovává zprávy o něco podrobněji:  
  
 ![Diagram znázorňující tok zpráv hostitele služby pracovního postupu.](./media/workflow-service-host-internals/workflow-service-host-message-flow.gif)  
  
 Tento diagram znázorňuje tři různé koncové body, koncový bod aplikace, koncový bod pracovního postupu ovládacího prvku a hostování koncový bod pracovního postupu. Koncový bod aplikace přijímá zprávy, které jsou vázány pro instanci konkrétního pracovního postupu. Kontrolní koncový bod pracovního postupu čeká operace u ovládacího prvku. Pracovní postup, který je hostitelem koncového bodu čeká na zprávy, které způsobují <xref:System.ServiceModel.WorkflowServiceHost> načíst a spustit bez služby pracovních postupů. Jak je znázorněno diagramu všechny zprávy se zpracovávají prostřednictvím modul runtime WCF.  Omezení instance služby pracovního postupu můžete dosáhnout použitím <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> vlastnost. Tato vlastnost bude omezovat počet instancí služby souběžných pracovních postupů. Překročení tohoto omezení je všechny další požadavky pro nové instance služby pracovního postupu nebo žádosti o aktivaci instance trvalá pracovního postupu se zařadí do fronty. Požadavky ve frontě se zpracovávají v pořadí FIFO bez ohledu na to, zda jsou požadavky na novou instanci nebo instance spuštěné, trvalý. Informace o zásadách hostitele je načtena, která určuje, jak jsou řešeny neošetřené výjimky a jak nečinných pracovních postupů služby jsou odpojeno a zachována. Další informace o těchto tématech naleznete v tématu [jak: Pracovní postup konfigurace chování neošetřené výjimky pomocí třídy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) a [jak: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md). Instance pracovního postupu jsou trvalé podle zásad hostiteli a jsou znovu načíst v případě potřeby. Další informace o pracovním postupu trvalosti najdete v tématu: [Postupy: Konfigurace trvalosti pomocí WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md), a [trvalost pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 Následující obrázek znázorňuje tok, když je zavolána WorkflowServiceHost.Open:  
  
 ![Diagram zobrazuje tok, když je volána WorkflowServiceHost.Open.](./media/workflow-service-host-internals/workflow-service-host-open.gif)  
  
 Pracovní postup načtení z XAML a vytvoření stromu aktivit. <xref:System.ServiceModel.WorkflowServiceHost> provede stromu aktivit a vytvoří popisu služby. Konfigurace se použije na hostiteli. Nakonec hostitele začne přijímat příchozí zprávy.  
  
 Následující obrázek znázorňuje, co <xref:System.ServiceModel.WorkflowServiceHost> provede, když přijme zprávu mez pro aktivitu Receive, která má CanCreateInstance nastavena na `true`:  
  
 ![Rozhodovací strom použitý objektem WFS hostitele, pokud obdrží zprávu a CanCreateInstance má hodnotu true.](./media/workflow-service-host-internals/workflow-service-host-receive-message-cancreateinstance.gif)  
  
 Zpráva dorazí a zpracovává zásobníku kanál WCF. Omezení se kontroluje a že jsou provedeny korelačních dotazů. Pokud zpráva je vázán k existující instanci se doručí zprávu. Pokud je potřeba vytvořit novou instanci, vlastnost CanCreateInstance aktivity Receive je zaškrtnuté políčko. Pokud je nastavena na hodnotu true, je vytvořena nová instance a zpráva doručena.  
  
 Následující obrázek znázorňuje, co <xref:System.ServiceModel.WorkflowServiceHost> provede, když přijme zprávu mez pro aktivitu Receive, která má CanCreateInstance nastavenou na hodnotu false.  
  
 ![Rozhodovací strom použitý objektem WFS hostitele, pokud obdrží zprávu a CanCreateInstance má hodnotu false.](./media/workflow-service-host-internals/workflow-service-host-receive-message.gif)  
  
 Zpráva dorazí a zpracovává zásobníku kanál WCF. Omezení se kontroluje a že jsou provedeny korelačních dotazů. Zprávu je vázán k existující instanci (protože CanCreateInstance má hodnotu false) tak, aby instance je načten z úložiště pro trvalé, záložka se obnoví a spustí pracovní postup.  
  
> [!WARNING]
> Hostitel služby pracovního postupu se nepodaří otevřít, pokud je SQL Server nakonfigurovaný tak, aby naslouchala na pouze protokol pojmenovaného kanálu.  
  
## <a name="see-also"></a>Viz také:

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Hostování služeb pracovních postupů](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)
- [Kontrolní koncový bod pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)
- [Postupy: Pracovní postup konfigurace chování neošetřené výjimky pomocí třídy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)
- [Vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [Trvalost pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
