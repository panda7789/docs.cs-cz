---
title: OverloadGroups
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c866d337b6e02fa18241b6fafd9d4e5a397ef69
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="overloadgroups"></a>OverloadGroups
Tato ukázka se skládá z aktivity (`CreateLocation`), která má dva zajímavé vlastnosti:  
  
1.  Je to některé požadováno, argumentů a ty, které jsou některé volitelné.  
  
2.  Umožňuje uživateli rozhodnout pro poskytnutí jednou ze dvou různých sad argumentů.  
  
 Tyto chování se dá udělat pomocí tyto dvě funkce:  
  
-   `[isRequired]`ověří, že vlastnost konkrétní aktivity je přiřadit, a pokud ne, vyvolá výjimku.  
  
-   `[OverloadGroup]`tak, aby uživatel aktivity můžete zvolit použití jedné množiny nebo jiné umístí společně sadu argumentů. Uživatel nemůže použít argumenty z různých skupin přetížení ve stejné instanci.  
  
 Po nastavení jiné pracovní postupy, volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> která vrací <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.Constraint>. Tisk <xref:System.Activities.Validation.Constraint> objekty do konzoly.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete **OverloadGroups.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavení a spuštění řešení.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
