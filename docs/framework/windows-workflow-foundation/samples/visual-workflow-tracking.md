---
title: Vizuální sledování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: 7433d2497b9a9993093e13e88e073fb40403e3b6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43803877"
---
# <a name="visual-workflow-tracking"></a>Vizuální sledování pracovního postupu
Tato ukázka předvádí, jak psát visual pracovního postupu pro sledování aplikací pomocí funkce pro ladění k dispozici prostřednictvím [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Aplikace spouští pracovní postup jednoduchý vývojový diagram (definováno v Workflow.xaml) a znovu je hostitelem návrháře postupu provádění zobrazit aktuálně prováděné pracovního postupu. Při spuštění pracovního postupu aktuálně spouštěné aktivity se zobrazí se žlutá šipka osnovy a ladění. Kromě toho sledování záznamů vygenerovaných tímto pracovním postupem se také zobrazí v okně aplikace. Další informace o sledování pracovního postupu najdete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Další informace o opětovné hostování návrháře postupu provádění zobrazit [změna hostování návrháře postupu provádění](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md).  
  
 Simulátor pracovních postupů funguje tak, že zachování dvě slovníky. Jeden obsahuje mapování mezi aktuálně prováděné objekt aktivity a číslo řádku XAML, ve kterém je vytvořena instance aktivity. Druhý obsahuje mapování mezi ID instance aktivity a objekt aktivity. Když jsou vydávány sledování záznamů pomocí vlastní profil sledování tracking profile, aplikace určuje ID instance aktuálně spouštěné aktivity a mapuje zpět do souboru XAML, která je vytvořena instance. Návrhář postupu provádění se změněným hostováním pak vydal pokyn ke zvýraznění aktivity na návrhové ploše a použít stejným způsobem jako pracovní postup ladicího programu, konkrétně kreslení žluté ohraničení kolem aktivity a zobrazení žlutá šipka sledovat levému okraji Návrhář.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete soubor WorkflowSimulator.sln z adresáře ukázka v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
3.  Stisknutím CTRL + F5 ke spuštění ukázky. Soubor Workflow.xaml zobrazí v okně návrháře postupu provádění se změněným hostováním.  
  
4.  Klikněte na tlačítko **souboru** nabídky a vybereme **spustit pracovní postup...** .  
  
5.  Všimněte si, že aktuálně spouštěné aktivity je zvýrazněn, jak je popsáno výše a sledování záznamů se zobrazí na pravé straně okna aplikace.  
  
6.  Po dokončení pracovního postupu, klikněte na možnost žádné záznamy sledování, chcete-li prověřit aktivity, které odpovídá.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`