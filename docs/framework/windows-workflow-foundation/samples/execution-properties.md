---
title: Vlastnosti spuštění
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 4906c2ad11c8b5822764435d2b39a5b51f2673ba
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409086"
---
# <a name="execution-properties"></a>Vlastnosti spuštění
Tato ukázka předvádí, jak definovat a používat vlastnost spuštění ve vlastní aktivity. V tomto příkladu provádění vlastnost určuje barvu popředí v konzole. Příklad pracovního postupu ukazuje, jak různé logické cesty spuštění (větve z <xref:System.Activities.Statements.Parallel> aktivity) můžete udržovat různé konzoly barvy bez ohledu na prokládaného spouštění funkcí s aktivit (mezi větvemi z <xref:System.Activities.Statements.Parallel> aktivit).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Otevřete v ukázkovém řešení ExecutionProperties.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    > [!NOTE]
    >  Zobrazení ThreeColors.xaml před sestavením řešení zobrazí chybu, protože používá vlastní aktivity musí být sestaveny ve stejnou dobu jako řešení.  
  
2.  Sestavte a spusťte řešení.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`