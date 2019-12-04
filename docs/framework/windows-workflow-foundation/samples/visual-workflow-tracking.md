---
title: Vizuální sledování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: 05f8fcf4c765998fc4e101d9dbef026d85b8b2fb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715506"
---
# <a name="visual-workflow-tracking"></a>Vizuální sledování pracovního postupu
Tato ukázka předvádí, jak napsat aplikaci pro sledování vizuálního pracovního postupu pomocí funkce ladění, která je dostupná prostřednictvím [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].

## <a name="sample-details"></a>Podrobnosti ukázky
 Aplikace spustí jednoduchý pracovní postup vývojového diagramu (definovaný v souboru Workflow. XAML) a znovu hostuje návrháře pracovních postupů, aby zobrazil aktuálně spuštěný pracovní postup. Při spuštění pracovního postupu se aktuálně vykonávaná aktivita zobrazuje se žlutým obrysem a šipkou ladění. Kromě toho se v okně aplikace zobrazují také záznamy o sledování vygenerované pracovním postupem. Další informace o sledování pracovního postupu najdete v tématu [sledování a trasování pracovních postupů](../workflow-tracking-and-tracing.md). Další informace o opětovném hostování návrháře pracovních postupů naleznete v tématu [rehostování Návrhář postupu provádění](../rehosting-the-workflow-designer.md).

 Simulátor pracovního postupu funguje tak, že udržuje dva slovníky. Jeden obsahuje mapování mezi aktuálně prováděným objektem aktivity a číslem řádku XAML, ve kterém je vytvořena instance aktivity. Druhý obsahuje mapování mezi ID instance aktivity a objekt aktivity. Když jsou záznamy sledování vydávány pomocí vlastního profilu sledování, aplikace určí ID instance aktuálně prováděné aktivity a namapuje ji zpět do souboru XAML, který vytvořil instanci. Návrhář pracovního postupu pro opětovné hostování pak vydá pokyn k zdůraznění aktivity na návrhové ploše a použití stejné metody jako ladicí program pracovního postupu, konkrétně pro vykreslení žlutého ohraničení kolem aktivity a zobrazení žluté šipky podél levé strany návrháře.

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Otevřete soubor WorkflowSimulator. sln z ukázkového adresáře v aplikaci Visual Studio 2010.

2. Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.

3. Stisknutím kombinace kláves CTRL + F5 ukázku spusťte. Tím se zobrazí soubor Workflow. XAML v okně návrháře přehostovaného pracovního postupu.

4. Klikněte na nabídku **soubor** a vyberte **Spustit pracovní postup...** .

5. Všimněte si, že aktuálně prováděná aktivita je zvýrazněná, jak je popsáno výše, a záznamy sledování se zobrazí na pravé straně okna aplikace.

6. Po dokončení pracovního postupu můžete kliknutím na kterýkoli ze záznamů sledování zkontrolovat, která aktivita odpovídá.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`
