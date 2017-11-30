---
title: "Ověření externích aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f45d4ffc04b206db0dfefbdbbe683146e09c767f
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="external-activity-validation"></a>Ověření externích aktivity
Tento příklad ukazuje, jak přidat logiku ověření do předdefinovaných aktivity, která nejsou autora. Logiku ověření se skládá z vynucení, který všechny <xref:System.Activities.Statements.If> aktivity k dispozici v pracovním postupu, musíte být jejich <xref:System.Activities.Statements.If.Then%2A> sada vlastností nebo jejich <xref:System.Activities.Statements.If.Else%2A> sadu vlastností. Navíc obsahuje logiku ověření kontrola, která všechny <xref:System.Activities.Statements.Pick> aktivity v pracovním postupu mají více než jeden větve, a pokud není tento případ, vygeneruje se upozornění.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Tato ukázka vytvoří pracovní postup s instancí každé aktivity ověřit: <xref:System.Activities.Statements.If> aktivity a <xref:System.Activities.Statements.Pick> aktivity. A <xref:System.Activities.Validation.Constraint> se vytvoří pro každou chování při ověřování. Omezení vytvořené v této ukázce jsou `ConstraintError_IfShouldHaveThenOrElse` a `ConstraintWarning_PickHasOneBranch`. V dalším kroku přidáte těchto omezení na `AdditionalConstraints` kolekce <xref:System.Activities.Validation.ValidationSettings> instance. Nakonec `static` <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> metodu <xref:System.Activities.Validation.ActivityValidationServices> je voláno k ověření aktivity v pracovním postupu a ověření výsledky budou vytištěny ke konzole.  
  
> [!NOTE]
>  Omezení zásad můžete přidat do žádné aktivity. Například můžete přidat zásady omezení <xref:System.Activities.Statements.Sequence> nebo <xref:System.Activities.Statements.Parallel> aktivity.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor ExternalActivityValidation.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte Ctrl + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`