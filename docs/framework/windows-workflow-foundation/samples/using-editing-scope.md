---
title: Použití oboru úprav
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 3e99610fda78e50f6d6eb72c38ecc82bdc96b5a2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715555"
---
# <a name="using-editing-scope"></a>Použití oboru úprav
Tato ukázka předvádí, jak provést dávku sady změn, aby mohly být vráceny v jedné atomické jednotce. Ve výchozím nastavení jsou akce provedené autorem návrháře aktivit automaticky integrovány do systému zpět/znovu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Úpravy oboru a akce zpět a znovu.  
  
## <a name="discussion"></a>Účely  
 Tato ukázka předvádí, jak dávkovat sadu změn do stromu <xref:System.Activities.Presentation.Model.ModelItem> v rámci jedné pracovní jednotky. Všimněte si, že při vytváření vazby na hodnoty <xref:System.Activities.Presentation.Model.ModelItem> přímo z Návrháře WPF se změny aplikují automaticky. Tato ukázka demonstruje, co je třeba provést, pokud je provedeno více dávkových změn prostřednictvím imperativního kódu namísto jedné změny.  
  
 V této ukázce jsou přidány tři aktivity. Při zahájení úprav je <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> volána na instanci <xref:System.Activities.Presentation.Model.ModelItem>. Změny provedené ve stromové struktuře <xref:System.Activities.Presentation.Model.ModelItem> v rámci tohoto oboru úprav jsou dávkově. Příkaz <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> vrátí <xref:System.Activities.Presentation.Model.EditingScope>, který lze použít k řízení této instance. <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> nebo <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> lze volat buď pro potvrzení, nebo pro obnovení rozsahu úprav.  
  
 Můžete také vnořovat <xref:System.Activities.Presentation.Model.EditingScope> objekty, což umožňuje sledovat více sad změn v rámci většího rozsahu úprav a lze je řídit individuálně. Scénář, který může být použit touto funkcí, by byl v případě, že změny z více dialogových oken musí být potvrzeny nebo vráceny samostatně, přičemž všechny změny jsou zpracovávány jako jediná atomická operace. V této ukázce jsou obory úprav skládané pomocí <xref:System.Collections.ObjectModel.ObservableCollection%601> typu <xref:System.Activities.Presentation.Model.ModelEditingScope>. <xref:System.Collections.ObjectModel.ObservableCollection%601> se používá, aby bylo možné pozorovat hloubku vnoření na návrhové ploše.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte a spusťte ukázku a potom pomocí tlačítek vlevo upravte pracovní postup.  
  
2. Klikněte na **otevřít rozsah úprav**.  
  
    1. Tento příkaz volá <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, která vytvoří obor úprav a vloží ho do sady úprav.  
  
    2. Do vybrané <xref:System.Activities.Presentation.Model.ModelItem>se pak přidají tři aktivity. Všimněte si, že pokud obor úprav nebyl otevřen pomocí <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, zobrazí se na plátně návrháře tři nové aktivity. Vzhledem k tomu, že tato operace stále čeká na vyřízení v rámci <xref:System.Activities.Presentation.Model.EditingScope>, Návrhář ještě není aktualizovaný.  
  
3. Kliknutím na **Zavřít rozsah** úprav potvrďte rozsah úprav. V návrháři se zobrazí tři aktivity.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
