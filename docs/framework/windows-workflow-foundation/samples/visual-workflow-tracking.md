---
title: Sledování Visual pracovního postupu
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: f010bdcf6004e84fd346d0e8649c87c008cad122
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516910"
---
# <a name="visual-workflow-tracking"></a>Sledování Visual pracovního postupu
Tento příklad znázorňuje způsob vytvoření visual pracovního postupu pro sledování aplikace pomocí funkce ladění, která je k dispozici prostřednictvím [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Aplikace spustí vývojový diagram jednoduché pracovního postupu (definovanou v Workflow.xaml) a znovu hostitelem návrháře pracovních postupů k zobrazení aktuálně prováděné pracovního postupu. Jako pracovní postup se spustí, zobrazí se aktuálně prováděné aktivity se žlutou šipku outline a ladění. Kromě toho sledování záznamy vygenerované pracovního postupu se také zobrazí v okně aplikace. Další informace o sledování pracovního postupu najdete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Další informace o opětovné hostování návrháře pracovních postupů najdete v tématu [opětovného hostování návrháře pracovních postupů](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md).  
  
 Simulátor pracovní postup funguje tak, že udržuje dva slovník. Jeden obsahuje mapování mezi objekt aktuálně prováděné aktivity a číslo řádku XAML, ve kterém je vytvořena instance aktivity. Druhý obsahuje mapování mezi ID instance aktivity a objekt aktivity. Při sledování záznamy jsou vygenerované pomocí vlastní sledování profil aplikace určuje ID instance aktuálně prováděné aktivity a mapuje zpět k souboru XAML, který je vytvořena instance. Návrháři opětovné hostování nástroje pracovních postupů je potom odeslán pokyn, zvýrazněte aktivitu na plochu návrháře a používat stejnou metodu jako pracovní postup ladicí program, konkrétně kreslení žlutý ohraničení aktivity a zobrazování žlutá šipka na levé straně Návrhář.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete soubor WorkflowSimulator.sln z adresáře ukázka v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
3.  Stisknutím kombinace kláves CTRL + F5 ke spuštění ukázky. Soubor Workflow.xaml zobrazí v okně návrháře opětovné hostování nástroje pracovního postupu.  
  
4.  Klikněte **soubor** nabídku a vyberte **spustit pracovní postup...** .  
  
5.  Všimněte si aktuálně prováděné aktivity se zvýrazní, jak je popsáno výše a sledování záznamy se zobrazí na pravé straně okna aplikace.  
  
6.  Po dokončení pracovního postupu, klikněte na možnost všechny záznamy sledování Kontrola aktivity, které odpovídá.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`