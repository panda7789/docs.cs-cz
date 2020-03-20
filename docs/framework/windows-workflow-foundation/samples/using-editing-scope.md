---
title: Použití oboru úprav
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 13f23289f0b764b80f971d3e514f3b12acfbfffc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142651"
---
# <a name="using-editing-scope"></a>Použití oboru úprav
Tato ukázka ukazuje, jak dávkové sadu změn tak, aby mohly být vrátit zpět v jedné atomické jednotky. Ve výchozím nastavení jsou akce provedené autorem návrháře aktivit automaticky integrovány do systému Vrátit nebo znovu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Úpravy oboru a vrátit a znovu.  
  
## <a name="discussion"></a>Diskuse  
 Tato ukázka ukazuje, jak dávkové <xref:System.Activities.Presentation.Model.ModelItem> sadu změn do stromu v rámci jedné jednotky práce. Všimněte si, <xref:System.Activities.Presentation.Model.ModelItem> že při vazbě na hodnoty přímo z návrháře WPF, změny jsou použity automaticky. Tato ukázka ukazuje, co je třeba udělat, když více změn, které mají být dávkové jsou prováděny prostřednictvím imperativní kód, nikoli jednu změnu.  
  
 V této ukázce jsou přidány tři aktivity. Při zahájení úprav <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> se nazývá instance <xref:System.Activities.Presentation.Model.ModelItem>aplikace . Změny provedené <xref:System.Activities.Presentation.Model.ModelItem> ve stromu v rámci tohoto oboru úprav jsou dávkově provedeny. Příkaz <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> vrátí <xref:System.Activities.Presentation.Model.EditingScope>, který lze použít k řízení této instance. Buď <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> nebo může být volána buď potvrdit nebo vrátit obor úprav.  
  
 Můžete také <xref:System.Activities.Presentation.Model.EditingScope> vnořit objekty, což umožňuje sledovat více sad změn jako součást většího oboru úprav a lze je ovládat jednotlivě. Scénář, který může používat tuto funkci by být, když změny z více dialogů musí být potvrzena nebo vrácena samostatně, se všemi změnami považovány za jednu atomickou operaci. V této ukázce jsou obory <xref:System.Collections.ObjectModel.ObservableCollection%601> úprav <xref:System.Activities.Presentation.Model.ModelEditingScope>skládané pomocí typu . Používá <xref:System.Collections.ObjectModel.ObservableCollection%601> se tak, aby hloubka vnoření mohla být pozorována na povrchu návrháře.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Vytvořte a spusťte ukázku a potom pomocí tlačítek na levé straně upravte pracovní postup.  
  
2. Klepněte na **tlačítko Otevřít obor úprav**.  
  
    1. Tento příkaz <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> volá, který vytvoří obor úprav a odešle jej do zásobníku úprav.  
  
    2. K vybranému souboru <xref:System.Activities.Presentation.Model.ModelItem>jsou přidány tři aktivity . Všimněte si, že pokud obor <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>úpravy nebyl otevřen s , tři nové aktivity se zobrazí na plátně návrháře. Vzhledem k tomu, <xref:System.Activities.Presentation.Model.EditingScope>že tato operace je stále čeká na vyřízení v rámci , návrháře ještě není aktualizován.  
  
3. Stisknutím **klávesy Zavřít obor úprav** potvrďte obor úprav. V návrháři se zobrazí tři aktivity.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
