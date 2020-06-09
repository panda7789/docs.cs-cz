---
title: Interní informace o hostiteli služby pracovního postupu
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: 7b47293211ee8143b1ce713c64ff1d5b22161b45
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594878"
---
# <a name="workflow-service-host-internals"></a>Interní informace o hostiteli služby pracovního postupu
<xref:System.ServiceModel.WorkflowServiceHost>poskytuje hostitele pro služby pracovního postupu. Zodpovídá za naslouchání příchozích zpráv a jejich směrování do příslušné instance služby pracovního postupu, řídí uvolnění a uchování nečinných pracovních postupů a další. Toto téma popisuje, jak třída WorkflowServiceHost zpracovává příchozí zprávy.  
  
## <a name="workflowservicehost-overview"></a>Přehled služby WorkflowServiceHost  

<xref:System.ServiceModel.WorkflowServiceHost>Třída se používá k hostování služeb pracovních postupů. Naslouchá příchozím zprávám a směruje je do příslušné instance služby, vytváří nové instance nebo načítá existující instance z trvalého úložiště podle potřeby. Následující diagram znázorňuje na vysoké úrovni, jak <xref:System.ServiceModel.WorkflowServiceHost> funguje:
  
 ![Diagram, který zobrazuje přehled hostitele služby pracovního postupu.](./media/workflow-service-host-internals/workflow-service-host-high-level-overview.gif)  
  
 Tento diagram znázorňuje, že <xref:System.ServiceModel.WorkflowServiceHost> načítá definice služby pracovního postupu ze souborů. xamlx a načítá konfigurační informace z konfiguračního souboru. Také načte konfiguraci sledování z profilu sledování. <xref:System.ServiceModel.WorkflowServiceHost>zveřejňuje řídicí koncový bod pracovního postupu, který umožňuje odesílat operace řízení instancím pracovních postupů.  Další informace najdete v tématu [Ukázka řídicího bodu pracovního postupu](workflow-control-endpoint.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost>také zveřejňuje koncové body aplikace, které naslouchají příchozím zprávám aplikace. Když se příchozí zpráva dorazí, pošle se do příslušné instance služby pracovního postupu (Pokud je aktuálně načtená). V případě potřeby se vytvoří nová instance pracovního postupu. Nebo pokud byla existující instance trvalá, načte se z úložiště trvalosti.  
  
## <a name="workflowservicehost-details"></a>Podrobnosti o hostiteli  
 Následující diagram ukazuje, jak <xref:System.ServiceModel.WorkflowServiceHost> zpracovává zprávy v dalších podrobnostech:  
  
 ![Diagram znázorňující tok zpráv hostitele služby pracovního postupu.](./media/workflow-service-host-internals/workflow-service-host-message-flow.gif)  
  
 Tento diagram znázorňuje tři různé koncové body, koncový bod aplikace, koncový bod řídicího bodu pracovního postupu a koncový bod hostující pracovní postup. Koncový bod aplikace přijímá zprávy vázané na konkrétní instanci pracovního postupu. Řídicí koncový bod pracovního postupu naslouchá operacím řízení. Koncový bod hostující pracovní postup naslouchá zprávám, které <xref:System.ServiceModel.WorkflowServiceHost> mají za následek načtení a spuštění pracovních postupů bez služby. Jak je znázorněno v diagramu všechny zprávy jsou zpracovávány pomocí modulu runtime WCF.  Omezování instancí služby pracovního postupu se dosahuje pomocí <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> Vlastnosti. Tato vlastnost omezí počet souběžných instancí služby pracovního postupu. Když se toto omezení překročí, všechny další požadavky na nové instance služby pracovního postupu nebo žádosti o aktivaci trvalých instancí pracovního postupu se zařadí do fronty. Požadavky ve frontě jsou zpracovávány v pořadí FIFO bez ohledu na to, zda se jedná o požadavky na novou instanci nebo spuštěnou, trvalou instanci. Načítají se informace o zásadách hostitele, které určují, jak se neošetřené výjimky účtují, a jak jsou nečinné služby pracovních postupů nenačteny a trvalé. Další informace o těchto tématech najdete v tématu [Postupy: Konfigurace chování neošetřené výjimky pracovního postupu s funkcí WorkflowServiceHost](config-workflow-unhandled-exception-workflowservicehost.md) a [Postupy: Konfigurace chování při nečinnosti pomocí funkce WorkflowServiceHost](how-to-configure-idle-behavior-with-workflowservicehost.md). Instance pracovních postupů jsou trvalé podle zásad hostitele a v případě potřeby jsou znovu načteny. Další informace o trvalosti pracovního postupu najdete v tématu: [Postupy: Konfigurace trvalosti pomocí hostitele WorkflowServiceHost](how-to-configure-persistence-with-workflowservicehost.md), [Vytvoření dlouhotrvající služby pracovního postupu](creating-a-long-running-workflow-service.md)a [trvalosti pracovního postupu](../../windows-workflow-foundation/workflow-persistence.md).  
  
 Následující ilustrace znázorňuje tok při volání metody WorkflowServiceHost. Open:  
  
 ![Diagram, který zobrazuje tok při volání metody WorkflowServiceHost. Open.](./media/workflow-service-host-internals/workflow-service-host-open.gif)  
  
 Pracovní postup je načten z XAML a je vytvořen strom aktivit. <xref:System.ServiceModel.WorkflowServiceHost>provede strom aktivity a vytvoří popis služby. Konfigurace se aplikuje na hostitele. Nakonec hostitel začne naslouchat příchozím zprávám.  
  
 Následující obrázek ukazuje, co <xref:System.ServiceModel.WorkflowServiceHost> dělá, když obdrží zprávu vázaný na aktivitu Receive s CanCreateInstance nastavenou na `true` :  
  
 ![Rozhodovací strom používaný hostitelem WFS, když obdrží zprávu a CanCreateInstance má hodnotu true.](./media/workflow-service-host-internals/workflow-service-host-receive-message-cancreateinstance.gif)  
  
 Zpráva se dorazí a zpracuje se v zásobníku kanálu WCF. Jsou zaškrtnuta omezení a jsou spuštěny korelační dotazy. Pokud je zpráva vázaná pro existující instanci, zpráva se doručí. Pokud je třeba vytvořit novou instanci, je zaškrtnuta vlastnost CanCreateInstance aktivity Receive. Pokud je nastavená na true, vytvoří se nová instance a zpráva se doručí.  
  
 Následující obrázek ukazuje, co <xref:System.ServiceModel.WorkflowServiceHost> dělá, když obdrží zprávu vázaný na aktivitu Receive s CanCreateInstance nastavenou na hodnotu false.  
  
 ![Rozhodovací strom používaný hostitelem WFS při přijetí zprávy a CanCreateInstance je false.](./media/workflow-service-host-internals/workflow-service-host-receive-message.gif)  
  
 Zpráva se dorazí a zpracuje se v zásobníku kanálu WCF. Jsou zaškrtnuta omezení a jsou spuštěny korelační dotazy. Zpráva je vázána pro existující instanci (protože CanCreateInstance má hodnotu false), takže je instance načtena z úložiště trvalosti, záložka je obnovena a pracovní postup se spustí.  
  
> [!WARNING]
> Hostitel služby pracovního postupu se nepodaří otevřít, pokud je SQL Server nakonfigurovaná tak, aby naslouchala jenom protokolu pojmenovaný kanál.  
  
## <a name="see-also"></a>Viz také

- [Služby pracovních postupů](workflow-services.md)
- [Hostování služeb pracovních postupů](hosting-workflow-services.md)
- [Kontrolní koncový bod pracovního postupu](workflow-control-endpoint.md)
- [Postupy: Konfigurace chování neošetřené výjimky pracovního postupu pomocí WorkflowServiceHost](config-workflow-unhandled-exception-workflowservicehost.md)
- [Vytvoření dlouhodobé služby pracovního postupu](creating-a-long-running-workflow-service.md)
- [Trvalost pracovního postupu](../../windows-workflow-foundation/workflow-persistence.md)
