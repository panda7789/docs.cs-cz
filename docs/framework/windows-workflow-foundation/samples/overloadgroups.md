---
title: OverloadGroups
ms.date: 03/30/2017
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
ms.openlocfilehash: 0773e76d36b25ad5485cc8912c7012815412de9f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514133"
---
# <a name="overloadgroups"></a>OverloadGroups
Tento příklad se skládá z aktivity (`CreateLocation`), která má dvě zajímavé vlastnosti:  
  
1.  Některé vyžaduje se argumentů a některé volitelné ty.  
  
2.  Umožňuje uživateli zvolit poskytnout dvě různé sady argumentů.  
  
 Tyto chování můžete provést pomocí těchto dvou funkcí:  
  
-   `[isRequired]` ověřuje, že vlastnost konkrétní aktivity je přiřadit, a pokud ne, dojde k výjimce.  
  
-   `[OverloadGroup]` umístí společně sadu argumentů, abyste uživatele aktivity můžete zvolit použití jedné sady nebo jiného. Uživatele nelze použít argumenty z různých skupin přetížit ve stejné instanci.  
  
 Po nastavení různých pracovních postupů, volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> který vrátí hodnotu <xref:System.Activities.Validation.ValidationResults> kolekce <xref:System.Activities.Validation.Constraint>. Tisk <xref:System.Activities.Validation.Constraint> objekty do konzoly.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Otevřít **OverloadGroups.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte a spusťte řešení.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
