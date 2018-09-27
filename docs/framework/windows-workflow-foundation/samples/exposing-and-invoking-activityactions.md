---
title: Zveřejnění a vyvolání akcí aktivit
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 99207c33d82ec9028da2355cc792c366dc5e0cc6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47398560"
---
# <a name="exposing-and-invoking-activityactions"></a>Zveřejnění a vyvolání akcí aktivit
Tato ukázka předvádí, jak vyvinout vlastní aktivity, která má <xref:System.Activities.ActivityAction>. Také ukazuje, jak tuto aktivitu použijte, tím, že poskytuje implementace <xref:System.Activities.ActivityAction>.  
  
 <xref:System.Activities.ActivityAction> Umožňuje autorovi aktivity vystavit "otvorů" konkrétní podpisy kde aktivity uživatele můžete zařadit vlastní chování. Například <xref:System.Activities.Statements.ForEach%601> aktivity (která funguje v kolekci položek), má <xref:System.Activities.ActivityAction> , který umožňuje uživateli aktivity k chování, které působí na aktuální položku iterace.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Otevřít **ActivityAction.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte a spusťte řešení.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`