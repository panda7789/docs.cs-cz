---
title: Ověření vztahy aktivity
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: e6dd0e6a7b48444073ebae378e21c1b45977a1f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515105"
---
# <a name="activity-relationships-validation"></a>Ověření vztahy aktivity
Tato ukázka se skládá ze tří aktivity `CreateCity`, `CreateState`, a `CreateCountry`. `CreateCity` musí být uvnitř `CreateState` aktivitu, a `CreateState` musí být uvnitř `CreateCountry` aktivity. V tomto příkladu je logiku ověření v kódu `CreateState` aktivitu a v jazyce XAML pro `CreateCity` aktivity. Obě omezení mít stejné chování.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Poskytuje následující tři aktivity pomocné rutiny, které umožňuje vývojářům ověření vztahy mezi aktivitami:  
  
 <xref:System.Activities.Validation.GetParentChain>  
 Poskytuje kolekci všechny aktivity, které patří do nadřazené aktuálního uzlu  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 Poskytuje kolekci všechny aktivity, které patří do stromu dílčí aktuální uzel, s výjimkou aktuálního uzlu  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 Poskytuje kolekci všechny aktivity ve stejném stromu pro jako aktuálního uzlu  
  
 V ukázce <xref:System.Activities.Statements.ForEach%601> aktivita se používá k provede kolekce vrácené <xref:System.Activities.Validation.GetParentChain>. Pro každý element v kolekci, je její typ porovnání s `CreateCountry` (nebo `CreateState` Pokud `CreateCity` je ověřován), a pokud je nalezena shoda příznak výsledek je nastaven na `true`. Nakonec <xref:System.Activities.Validation.AssertValidation> slouží ke generování chybu ověření, pokud je výsledek příznak nastaven na `false`.  
  
### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete ContainmentValidation.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení.  
  
3.  Stisknutím kláves CTRL + F5 spusťte program.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
