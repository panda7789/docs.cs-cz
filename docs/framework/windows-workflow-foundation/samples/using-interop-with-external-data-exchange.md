---
title: Pomocí zprostředkovatele komunikace se serverem Exchange externích dat
ms.date: 03/30/2017
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
ms.openlocfilehash: 9571a571137ff0a493be67ee9c607cd46dd47889
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-interop-with-external-data-exchange"></a>Pomocí zprostředkovatele komunikace se serverem Exchange externích dat
<xref:System.Activities.Statements.Interop> Aktivity můžete použít ke spuštění aktivity z Windows Workflow Foundation (WF) v [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] a [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) a pracovních postupů v rámci modelu Windows Workflow Foundation v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4). Tento příklad ukazuje, jak nakonfigurovat a spustit WF3 pracovní postup, který používá <xref:System.Workflow.Activities.ExternalDataExchangeService> (a odpovídající vlastní aktivity pro volání metod a zpracování událostí) pomocí <xref:System.Activities.Statements.Interop> aktivity v WF4 služby pracovních postupů.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete soubor ExternalDataExchange.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Chcete-li sestavit ukázku, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit ukázku, stisknutím klávesy F5.
