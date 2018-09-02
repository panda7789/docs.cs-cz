---
title: Použití oboru úprav
ms.date: 03/30/2017
ms.assetid: 79306f9e-318b-4687-9863-8b93d1841716
ms.openlocfilehash: 268849c584c235a21a0818baa60f119cf8e49305
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419981"
---
# <a name="using-editing-scope"></a>Použití oboru úprav
Tento příklad ukazuje, jak batch sady změn, takže se můžete vrátit zpět v jednu atomickou jednotku. Ve výchozím nastavení jsou akce prováděné návrháře autorem aktivity automaticky integrované do systému zpět/znovu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Úpravy rozsahu a zpět a znovu.  
  
## <a name="discussion"></a>Diskuse  
 Tento příklad ukazuje, jak batch sada změn <xref:System.Activities.Presentation.Model.ModelItem> stromové struktury v rámci jedné jednotky práce. Všimněte si, že při vytváření vazby na <xref:System.Activities.Presentation.Model.ModelItem> hodnoty přímo z Návrháře WPF, změny se použijí automaticky. Tento příklad ukazuje, co je třeba provést při více změn ve službě sjednotit se provádějí pomocí imperativního kódu, spíše než jediné změny.  
  
 V této ukázce jsou přidány tři aktivity. Po zahájení úpravy <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> je volán na instanci <xref:System.Activities.Presentation.Model.ModelItem>. Změny provedené <xref:System.Activities.Presentation.Model.ModelItem> stromové struktury v rámci tohoto rozsahu úprav jsou dávce. <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> Příkazem <xref:System.Activities.Presentation.Model.EditingScope>, které lze použít k ovládání této instance. Buď <xref:System.Activities.Presentation.Model.EditingScope.OnComplete%2A> nebo <xref:System.Activities.Presentation.Model.EditingScope.OnRevert%2A> lze volat buď potvrzení nebo vrátit zpět úpravy rozsahu.  
  
 Lze také vnořit <xref:System.Activities.Presentation.Model.EditingScope> objekty, které umožňuje více sad změn ke sledování v rámci větší úpravy rozsahu a je možné řídit samostatně. Tento scénář může pomocí této funkce se při změny z více dialogů musí být potvrzené nebo vrátit samostatně, všechny změny se zachází jako jednu atomickou operaci. V této ukázce jsou uspořádány vedle pomocí úpravy oborů <xref:System.Collections.ObjectModel.ObservableCollection%601> typu <xref:System.Activities.Presentation.Model.ModelEditingScope>. <xref:System.Collections.ObjectModel.ObservableCollection%601> Se používá tak, aby hloubka vnoření může být dodržen na návrhové ploše.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Sestavení a spuštění ukázky a potom pomocí tlačítek na levé straně upravte pracovní postup.  
  
2.  Klikněte na tlačítko **otevřete oboru úprav**.  
  
    1.  Tento příkaz volá <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A> , který vytvoří úpravy rozsahu a nasdílí změny do úprav zásobníku.  
  
    2.  Tři aktivity se pak přidají do vybraného <xref:System.Activities.Presentation.Model.ModelItem>. Všimněte si, že pokud rozsahu úprav, kdyby byl otevřen s <xref:System.Activities.Presentation.Model.ModelItem.BeginEdit%2A>, by se zobrazí tři nové aktivity na plátně návrháře. Protože tato operace je stále čekají v rámci <xref:System.Activities.Presentation.Model.EditingScope>, Návrhář není ještě neaktualizovaly.  
  
3.  Stisknutím klávesy **zavřít úpravy rozsahu** potvrdit rozsahu úprav. Tři aktivity se zobrazí v návrháři.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\UsingEditingScope`
