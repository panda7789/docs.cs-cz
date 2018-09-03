---
title: Pomocí rozhraní .NET Framework 3.0 nebo .NET Framework 3.5 aktivity v pracovním postupu rozhraní .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
ms.openlocfilehash: ec44e56a99660ba422c73bbbf00bf5ef6b7b61ff
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486128"
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a>Pomocí rozhraní .NET Framework 3.0 nebo .NET Framework 3.5 aktivity v pracovním postupu rozhraní .NET Framework 4.5
<xref:System.Activities.Statements.Interop> Aktivity umožňuje spuštění aktivity rozhraní .NET Framework 3.0 Windows Workflow Foundation (WF) v rámci [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] pracovního postupu. Tato ukázka předvádí, jak používat <xref:System.Activities.Statements.Interop> aktivity předat řetězec jako argument pro vlastní [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] aktivity.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení SimpleInterop.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a>Viz také
