---
title: Vizuální sledování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: 6e87b0ef5a0d6fa97c87c99a63fe0e23c389140c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772840"
---
# <a name="visual-workflow-tracking"></a>Vizuální sledování pracovního postupu
Tato ukázka předvádí, jak psát visual pracovního postupu pro sledování aplikací pomocí funkce pro ladění k dispozici prostřednictvím [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].

## <a name="sample-details"></a>Ukázka podrobnosti
 Aplikace spouští pracovní postup jednoduchý vývojový diagram (definováno v Workflow.xaml) a znovu je hostitelem návrháře postupu provádění zobrazit aktuálně prováděné pracovního postupu. Při spuštění pracovního postupu aktuálně spouštěné aktivity se zobrazí se žlutá šipka osnovy a ladění. Kromě toho sledování záznamů vygenerovaných tímto pracovním postupem se také zobrazí v okně aplikace. Další informace o sledování pracovního postupu najdete v tématu [pracovního postupu pro sledování a trasování](../workflow-tracking-and-tracing.md). Další informace o opětovné hostování návrháře postupu provádění zobrazit [změna hostování návrháře postupu provádění](../rehosting-the-workflow-designer.md).

 Simulátor pracovních postupů funguje tak, že zachování dvě slovníky. Jeden obsahuje mapování mezi aktuálně prováděné objekt aktivity a číslo řádku XAML, ve kterém je vytvořena instance aktivity. Druhý obsahuje mapování mezi ID instance aktivity a objekt aktivity. Když jsou vydávány sledování záznamů pomocí vlastní profil sledování tracking profile, aplikace určuje ID instance aktuálně spouštěné aktivity a mapuje zpět do souboru XAML, která je vytvořena instance. Návrhář postupu provádění se změněným hostováním pak vydal pokyn ke zvýraznění aktivity na návrhové ploše a použít stejným způsobem jako pracovní postup ladicího programu, konkrétně kreslení žluté ohraničení kolem aktivity a zobrazení žlutá šipka sledovat levému okraji Návrhář.

#### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1. Otevřete soubor WorkflowSimulator.sln z adresáře ukázka v sadě Visual Studio 2010.

2. Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.

3. Stisknutím CTRL + F5 ke spuštění ukázky. Soubor Workflow.xaml zobrazí v okně návrháře postupu provádění se změněným hostováním.

4. Klikněte na tlačítko **souboru** nabídky a vybereme **spustit pracovní postup...** .

5. Všimněte si, že aktuálně spouštěné aktivity je zvýrazněn, jak je popsáno výše a sledování záznamů se zobrazí na pravé straně okna aplikace.

6. Po dokončení pracovního postupu, klikněte na možnost žádné záznamy sledování, chcete-li prověřit aktivity, které odpovídá.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`