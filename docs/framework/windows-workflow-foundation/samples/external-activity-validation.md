---
title: Ověřování externích aktivit
ms.date: 03/30/2017
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
ms.openlocfilehash: 4805bec3deed0779b02687b11dd487e673802925
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527804"
---
# <a name="external-activity-validation"></a>Ověřování externích aktivit
Tento příklad ukazuje, jak přidat logiku ověřování k předdefinovanou aktivitu, kterých nejste Autor. Logiku ověřování se skládá z vynucení všechny <xref:System.Activities.Statements.If> aktivity k dispozici v pracovním postupu, musíte být jejich <xref:System.Activities.Statements.If.Then%2A> sadu vlastností nebo jejich <xref:System.Activities.Statements.If.Else%2A> sadu vlastností. Navíc logiku ověřování zahrnuje kontrolu, která všechny <xref:System.Activities.Statements.Pick> aktivity, které jsou k dispozici v pracovním postupu mají více než jednu větev, a pokud to není tento případ, vygeneruje se upozornění.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Tato ukázka vytvoří pracovní postup s instancí každé aktivity ověřit: <xref:System.Activities.Statements.If> aktivity a <xref:System.Activities.Statements.Pick> aktivity. A <xref:System.Activities.Validation.Constraint> se vytvoří pro každou chování ověřování. Omezení, vytvořené v této ukázce jsou `ConstraintError_IfShouldHaveThenOrElse` a `ConstraintWarning_PickHasOneBranch`. V dalším kroku tato omezení jsou přidána do `AdditionalConstraints` kolekce <xref:System.Activities.Validation.ValidationSettings> instance. Nakonec `static` <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> metoda <xref:System.Activities.Validation.ActivityValidationServices> voláno k ověření aktivity v pracovním postupu a ověření jsou výsledky tisknout do konzoly.  
  
> [!NOTE]
>  Omezení zásad můžete přidat na aktivitu. Například můžete přidat omezení zásad a <xref:System.Activities.Statements.Sequence> nebo <xref:System.Activities.Statements.Parallel> aktivity.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor ExternalActivityValidation.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte Ctrl + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`