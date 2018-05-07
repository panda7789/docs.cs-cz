---
title: Základní ověřování
ms.date: 03/30/2017
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
ms.openlocfilehash: db7db339d0b7bfd756d8ba22fb8488b8f7ecfa3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="basic-validation"></a>Základní ověřování
Tato ukázka se skládá z aktivity, `CreateProduct`, který ověří, jestli jeho `Cost` argument je menší než nebo rovno jeho `Price` argument.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Existují dva autoři, které používají ověřování, Autor aktivity (vytvoří logiku ověření pro aktivitu) a Autor pracovního postupu, který volá služby ověřování v určitém pracovním postupu. V tomto scénáři chce autor aktivity vynutit, že každá instance svou činnost musí mít menší nebo rovna nákladech, než který ceny.  
  
 Musíte vytvořit aktivity (uvnitř aktivita):  
  
-   Vytvořit omezení (`PriceGreaterThanCost`). Toto je, kde se nachází všechny logiku ověření.  
  
-   Přepsání `System.Activities.CodeActivity.OnGetConstraints()` a přidat omezení (`PriceGreaterThanCost`) k omezení <xref:System.Collections.IList>.  
  
 Autor pracovního postupu (hlavní aplikace) musí:  
  
-   Vytvoření pracovního postupu s instancí aktivity k ověření (`CreateProduct`).  
  
-   Volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, která vrátí <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.ValidationError>.  
  
-   (Volitelné) Tisk <xref:System.Activities.Validation.ValidationError> objekty.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete BasicValidation.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavení a spuštění řešení.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`