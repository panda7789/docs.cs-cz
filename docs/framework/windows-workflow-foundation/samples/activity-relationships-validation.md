---
title: Ověřování relací mezi aktivitami
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: 50f08118fb5ad4d9b8fe809e7ab3cc5d57f28149
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556161"
---
# <a name="activity-relationships-validation"></a>Ověřování relací mezi aktivitami
Tento příklad se skládá ze tří činností `CreateCity`, `CreateState`, a `CreateCountry`. `CreateCity` musí být uvnitř `CreateState` aktivitu, a `CreateState` musí být uvnitř `CreateCountry` aktivity. Pro účely této ukázce logiku ověřování je v kódu `CreateState` aktivitu a v XAML pro `CreateCity` aktivity. Obě omezení mají stejné chování.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Poskytuje následující tři aktivity pomocné rutiny, které umožňuje vývojářům ověřit relací mezi aktivitami:  
  
 <xref:System.Activities.Validation.GetParentChain>  
 Obsahuje kolekci všech aktivit, které patří do nadřazeného aktuální uzel  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 Obsahuje kolekci všech aktivit, které patří do dílčí stromu pro aktuální uzel, s výjimkou aktuální uzel  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 Obsahuje kolekci všech aktivit ve stejném stromu pro jako aktuální uzel  
  
 V ukázce <xref:System.Activities.Statements.ForEach%601> aktivita se používá k provede kolekci vrácené poskytovatelem <xref:System.Activities.Validation.GetParentChain>. Pro každý prvek v kolekci, jeho typ je ve srovnání s `CreateCountry` (nebo `CreateState` Pokud `CreateCity` ověřován), a když se najde shoda výsledek příznak je nastaven na `true`. A konečně <xref:System.Activities.Validation.AssertValidation> se používá k vygenerování chyby ověřování, pokud výsledek příznak je nastaven na `false`.  
  
### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete v ukázkovém řešení ContainmentValidation.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení.  
  
3.  Stisknutím kláves CTRL + F5 spusťte program.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
