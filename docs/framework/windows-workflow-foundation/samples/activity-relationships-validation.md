---
title: "Ověření vztahy aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 03ac8e41f8126c6b05eac82d143291a0de491969
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="activity-relationships-validation"></a>Ověření vztahy aktivity
Tato ukázka se skládá ze tří aktivity `CreateCity`, `CreateState`, a `CreateCountry`. `CreateCity`musí být uvnitř `CreateState` aktivitu, a `CreateState` musí být uvnitř `CreateCountry` aktivity. V tomto příkladu je logiku ověření v kódu `CreateState` aktivitu a v jazyce XAML pro `CreateCity` aktivity. Obě omezení mít stejné chování.  
  
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`  
  
## <a name="see-also"></a>Viz také
