---
title: Typy omezení
ms.date: 03/30/2017
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
ms.openlocfilehash: 202a2c7b3a3fc400552e42c8606457964af66af2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401529"
---
# <a name="constraint-types"></a>Typy omezení
Tento příklad ukazuje dva různé způsoby použití omezení do pracovního postupu, jeden je uvnitř aktivity (build) a jeden je z mimo něj (zásady). V tomto scénáři chce autor aktivity (ze strany 3rth softwarovou společnost) ověření vztahu mezi dvěma argumenty. V tomto případě náklady na by měla být menší než nebo rovna hodnotě cena. Toto je omezení obecné ověření sestavení.  
  
 Potom kupte vlastník chce přidat nějaké ověření této obecné aktivitě. V případě jeho chce většinou produkty bude 9,99 USD nebo nižší. Ano, pomocí zásad omezení, které je nad `CreateProduct` aktivity.  
  
 V ukázce:  
  
 Musí být autorem aktivity (build):  
  
-   Vytvoření omezení (`PriceGreaterThanCost`). To je, ve které se nachází všechny logiku ověřování.  
  
-   Přepsat `System.Activities.CodeActivity.OnGetConstraints()` a přidat omezení (`PriceGreaterThanCost`) k omezením <xref:System.Collections.IList>.  
  
 Musí se vytvořit pracovní postup (zásady):  
  
-   Vytvoření pracovního postupu pomocí instance aktivity ověřit (`CreateProduct`).  
  
-   Vytvoření omezení (`MaxPrice`).  
  
-   Vytvoření <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) a přidat omezení (`MaxPrice`) do kolekce `AdditionalConstraints`. Tady Autor pracovního postupu můžete přidat omezení zásad pro všechny aktivity, jako je například pořadí nebo paralelní.  
  
-   Volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, který vrátí hodnotu <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.ValidationError> objekty.  
  
-   (Volitelné) Tisk <xref:System.Activities.Validation.ValidationError> objekty.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Otevřete v ukázkovém řešení ConstraintTypes.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte a spusťte řešení.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`