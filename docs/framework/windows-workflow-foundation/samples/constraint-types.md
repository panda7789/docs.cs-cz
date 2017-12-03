---
title: "Omezení typů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd73776aebb571fad732f554d6a96c1611506e8c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="constraint-types"></a>Omezení typů
Tento příklad ukazuje dva různé způsoby použití omezení do pracovního postupu, jedna je z uvnitř aktivity (sestavení) a jeden z mimo (zásady). V tomto scénáři chce autor aktivity (od výrobce 3rth softwarové společnosti) k ověření vztah mezi dva argumenty. V takovém případě náklady na by měla být menší než nebo rovna hodnotě cenu. Toto je omezení obecné ověření sestavení.  
  
 Potom obchod vlastníka chce přidat některé ověřování pro tuto aktivitu Obecné. V případě jeho chce většinu produkty být $9.99 nebo méně. Ano, pomocí zásad omezení, která je na `CreateProduct` aktivity.  
  
 V ukázce:  
  
 Musí se vytvořit aktivity (sestavení):  
  
-   Vytvořit omezení (`PriceGreaterThanCost`). Toto je, kde se nachází všechny logiku ověření.  
  
-   Přepsání `System.Activities.CodeActivity.OnGetConstraints()` a přidat omezení (`PriceGreaterThanCost`) k omezení <xref:System.Collections.IList>.  
  
 Musí se vytvořit pracovní postup (zásady):  
  
-   Vytvoření pracovního postupu s instancí aktivity k ověření (`CreateProduct`).  
  
-   Vytvořit omezení (`MaxPrice`).  
  
-   Vytvoření <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) a přidejte omezení (`MaxPrice`) do kolekce `AdditionalConstraints`. Zde Autor pracovního postupu můžete přidat omezení zásad pro všechny aktivity, například pořadí nebo paralelní.  
  
-   Volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, která vrátí <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.ValidationError> objekty.  
  
-   (Volitelné) Tisk <xref:System.Activities.Validation.ValidationError> objekty.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete ConstraintTypes.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavení a spuštění řešení.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`