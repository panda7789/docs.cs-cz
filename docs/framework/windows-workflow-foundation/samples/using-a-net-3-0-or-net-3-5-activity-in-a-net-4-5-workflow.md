---
title: Pomocí rozhraní .NET Framework 3.0 nebo rozhraní .NET Framework 3.5 aktivity v pracovním postupu rozhraní .NET Framework 4.5
ms.date: 03/30/2017
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
ms.openlocfilehash: ab2e93918617bd1ca21fb32878d446db0dd2ef16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a>Pomocí rozhraní .NET Framework 3.0 nebo rozhraní .NET Framework 3.5 aktivity v pracovním postupu rozhraní .NET Framework 4.5
<xref:System.Activities.Statements.Interop> Aktivity umožňuje spouštění rozhraní .NET Framework 3.0 Windows Workflow Foundation (WF) aktivitu v rámci [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] pracovního postupu. Tento příklad znázorňuje způsob použití <xref:System.Activities.Statements.Interop> aktivity předat jako argument řetězec vlastní [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] aktivity.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení SimpleInterop.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a>Viz také
