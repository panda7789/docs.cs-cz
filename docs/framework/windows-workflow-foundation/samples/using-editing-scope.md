---
title: Použití oboru úprav
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 386c94e5c6761bb704efc9e48723d0e91a4aaf6b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037803"
---
# <a name="using-editing-scope"></a>Použití oboru úprav
Tato ukázka předvádí, jak provést dávku sady změn, aby mohly být vráceny v jedné atomické jednotce. Ve výchozím nastavení jsou akce provedené autorem návrháře aktivit automaticky integrovány do systému zpět/znovu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Úpravy oboru a akce zpět a znovu.  
  
## <a name="discussion"></a>Účely  
 Tento příklad ukazuje, jak dávkovat sadu změn <xref:System.Activities.Presentation.Model.ModelItem> ve stromové struktuře v rámci jedné pracovní jednotky. Všimněte si, že při <xref:System.Activities.Presentation.Model.ModelItem> vytváření vazby na hodnoty přímo z Návrháře WPF se změny aplikují automaticky. Tato ukázka demonstruje, co je třeba provést, pokud je provedeno více dávkových změn prostřednictvím imperativního kódu namísto jedné změny.  
  
 V této ukázce jsou přidány tři aktivity. Při zahájení <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> úprav se volá na <xref:System.Activities.Presentation.Model.ModelItem>instanci. Změny provedené <xref:System.Activities.Presentation.Model.ModelItem> ve stromové struktuře v rámci tohoto oboru úprav jsou dávkově. <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> Příkaz<xref:System.Activities.Presentation.Model.EditingScope>vrátí, který lze použít k řízení této instance. Buď <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> nebo<xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> může být volána buď k potvrzení, nebo vrácení oboru úprav.  
  
 Můžete také vnořovat <xref:System.Activities.Presentation.Model.EditingScope> objekty, které umožňují sledovat více sad změn v rámci většího rozsahu úprav a lze je řídit individuálně. Scénář, který může být použit touto funkcí, by byl v případě, že změny z více dialogových oken musí být potvrzeny nebo vráceny samostatně, přičemž všechny změny jsou zpracovávány jako jediná atomická operace. V této ukázce jsou obory úprav skládané pomocí <xref:System.Collections.ObjectModel.ObservableCollection%601> typu. <xref:System.Activities.Presentation.Model.ModelEditingScope> <xref:System.Collections.ObjectModel.ObservableCollection%601> Je použit, aby bylo možné pozorovat hloubku vnoření na návrhové ploše.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte a spusťte ukázku a potom pomocí tlačítek vlevo upravte pracovní postup.  
  
2. Klikněte na **otevřít rozsah úprav**.  
  
    1. Tento příkaz volá <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> , který vytvoří obor úprav a vloží ho do editačního zásobníku.  
  
    2. Do vybrané <xref:System.Activities.Presentation.Model.ModelItem>části se pak přidají tři aktivity. Všimněte si, že pokud obor úprav nebyl otevřen s <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, zobrazí se na plátně návrháře tři nové aktivity. Vzhledem k tomu <xref:System.Activities.Presentation.Model.EditingScope>, že tato operace stále čeká na vyřízení v, Návrhář ještě není aktualizovaný.  
  
3. Kliknutím na **Zavřít rozsah** úprav potvrďte rozsah úprav. V návrháři se zobrazí tři aktivity.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
