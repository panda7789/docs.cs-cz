---
title: Pomocí úpravy rozsahu
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 67b79ebe558578ca612d59d48eb7ee291a6db501
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517388"
---
# <a name="using-editing-scope"></a>Pomocí úpravy rozsahu
Tento příklad znázorňuje postup dávky sadu změn, aby se můžete odvolat v jedné jednotky atomic. Ve výchozím nastavení jsou automaticky akce prováděné pomocí návrháře Autor aktivity integrované do systému zpět/opakování.  
  
## <a name="demonstrates"></a>Demonstruje  
 Úpravy rozsahu a zpět a znovu.  
  
## <a name="discussion"></a>Diskusní  
 Tento příklad ukazuje, jak dávky sadu změn <xref:System.Activities.Presentation.Model.ModelItem> stromové struktury v rámci jedné jednotky práce. Všimněte si, že při vytváření vazby k <xref:System.Activities.Presentation.Model.ModelItem> hodnoty přímo z Návrháře WPF, změny se použijí automaticky. Tento příklad znázorňuje, co je třeba provést při více zpracovat v dávce se změny prostřednictvím imperativní kódu, nikoli jediné změny.  
  
 V této ukázce se přidají tři aktivity. Po úpravě zahájení <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> se volá na instanci <xref:System.Activities.Presentation.Model.ModelItem>. Změny provedené <xref:System.Activities.Presentation.Model.ModelItem> stromové struktury v rámci oboru této úpravy jsou zpracovat v dávce. <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> Příkaz vrátí <xref:System.Activities.Presentation.Model.EditingScope>, které můžete použít k řízení této instance. Buď <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> nebo <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> lze volat pro buď potvrzení nebo vrátit zpět úpravy rozsahu.  
  
 Můžete také vnořovat <xref:System.Activities.Presentation.Model.EditingScope> objekty, které umožňuje sledovat jako součást větší úpravy více sad změny oboru a můžete řídit samostatně. Scénář, který mohou používat tuto funkci bude při změny z několika dialogová okna musí být potvrzen, nebo samostatně, vrátit zpět všechny změny, je považován za jeden atomické operace. V této ukázce jsou skládaný pomocí úpravy oborů <xref:System.Collections.ObjectModel.ObservableCollection%601> typu <xref:System.Activities.Presentation.Model.ModelEditingScope>. <xref:System.Collections.ObjectModel.ObservableCollection%601> Se používá, takže může být dodržen hloubka vnoření na plochu návrháře.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavení a spuštění vzorového a potom pomocí tlačítek vlevo upravit pracovní postup.  
  
2.  Klikněte na tlačítko **otevřete úpravách rozsahu**.  
  
    1.  Tento příkaz volá <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> , vytvoří úpravy rozsahu a doručí do úpravy zásobníku.  
  
    2.  Tři aktivity se pak přidají do vybraného <xref:System.Activities.Presentation.Model.ModelItem>. Všimněte si, že pokud úpravy rozsahu kdyby byla otevřena s <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, tři nové aktivity se zobrazí na plátna návrháře. Protože tato operace čekající na vyřízení je stále v rámci <xref:System.Activities.Presentation.Model.EditingScope>, návrháře není ještě neaktualizovaly.  
  
3.  Stiskněte klávesu **zavřít úpravy rozsahu** potvrzení úpravy rozsahu. Tři aktivity se zobrazí v návrháři.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
