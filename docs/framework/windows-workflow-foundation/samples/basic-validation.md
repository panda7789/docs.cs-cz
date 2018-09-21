---
title: Základní ověřování
ms.date: 03/30/2017
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
ms.openlocfilehash: 74d99e2d426e9ea5701fad80418fdf019112cc9e
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539470"
---
# <a name="basic-validation"></a>Základní ověřování
Tento příklad se skládá z aktivit, `CreateProduct`, který ověří, jestli jeho `Cost` argumentu je menší než nebo roven jeho `Price` argument.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Existují dva autorů, které používají ověřování, autorem aktivity (vytvoří logiku ověřování aktivity) a Autor pracovního postupu, který volá ověření služby na konkrétní pracovní postup. V tomto scénáři autorem aktivity chce zajistit, že každá instance jeho aktivity musí mít menší nebo rovna náklady než u cena.  
  
 Musí být autorem aktivity (v aktivitě):  
  
-   Vytvoření omezení (`PriceGreaterThanCost`). To je, ve které se nachází všechny logiku ověřování.  
  
-   Přepsat `System.Activities.CodeActivity.OnGetConstraints()` a přidat omezení (`PriceGreaterThanCost`) k omezením <xref:System.Collections.IList>.  
  
 Autor pracovního postupu (hlavní aplikace) musí:  
  
-   Vytvoření pracovního postupu pomocí instance aktivity ověřit (`CreateProduct`).  
  
-   Volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, který vrátí hodnotu <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.ValidationError>.  
  
-   (Volitelné) Tisk <xref:System.Activities.Validation.ValidationError> objekty.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Otevřete v ukázkovém řešení BasicValidation.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte a spusťte řešení.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`