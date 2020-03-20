---
title: Vizuální sledování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: 22c91a12bba148e1fa823bb2bf9b3eaf16704c46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182753"
---
# <a name="visual-workflow-tracking"></a>Vizuální sledování pracovního postupu
Tato ukázka ukazuje, jak napsat vizuální aplikace pro sledování pracovního postupu pomocí funkce ladění, které jsou [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]k dispozici prostřednictvím rozhraní .

## <a name="sample-details"></a>Podrobnosti ukázky
 Aplikace spustí jednoduchý pracovní postup vývojového diagramu (definovaného v souboru Workflow.xaml) a znovu hostuje návrháře pracovního postupu, aby zobrazil aktuálně spuštěný pracovní postup. Při provádění pracovního postupu je aktuálně spuštěná aktivita zobrazena se žlutou šipkou osnovy a ladicí šipkou. Kromě toho jsou v okně aplikace zobrazeny také záznamy sledování generované pracovním postupem. Další informace o sledování pracovního postupu naleznete v [tématu Sledování pracovního postupu a trasování](../workflow-tracking-and-tracing.md). Další informace o opětovném hostování návrháře pracovních postupů naleznete [v tématu Rehosting návrháře pracovních postupů](../rehosting-the-workflow-designer.md).

 Simulátor pracovního postupu funguje tak, že udržuje dva slovníky. Jeden obsahuje mapování mezi aktuálně prováděný objekt aktivity a číslo řádku XAML, ve kterém je aktivita vytvořena instance. Druhý obsahuje mapování mezi ID instance aktivity a objektem aktivity. Při sledování záznamů jsou vydávány pomocí vlastního profilu sledování, aplikace určuje ID instance aktuálně provádějící aktivity a mapuje zpět do souboru XAML, který ji instanci. Návrhář pracovního postupu rehosted je pak instruován, aby zvýraznil aktivitu na povrchu návrháře a použil stejnou metodu jako ladicí program pracovního postupu, konkrétně kreslení žlutého ohraničení kolem aktivity a zobrazení žluté šipky podél levé strany Návrhář.

#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek

1. Otevřete soubor WorkflowSimulator.sln z ukázkového adresáře v sadě Visual Studio 2010.

2. Stisknutím kláves CTRL+SHIFT+B řešení sestavíte.

3. Stisknutím kláves CTRL + F5 spusťte ukázku. Zobrazí se soubor Workflow.xaml v okně návrháře pracovního postupu s rehosted.

4. Klepněte na nabídku **Soubor** a vyberte **Spustit pracovní postup...**.

5. Všimněte si, že aktuálně spuštěná aktivita je zvýrazněna, jak je popsáno výše, a záznamy sledování jsou zobrazeny na pravé straně okna aplikace.

6. Po dokončení pracovního postupu můžete klepnutím na některý ze záznamů sledování zkontrolovat, které aktivitě odpovídá.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`
