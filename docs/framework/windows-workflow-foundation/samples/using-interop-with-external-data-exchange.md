---
title: Použití interoperability s výměnou externích dat
ms.date: 03/30/2017
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
ms.openlocfilehash: 534321e5b5568e0dd0988333dc98ccc18ff33df8
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577864"
---
# <a name="using-interop-with-external-data-exchange"></a>Použití interoperability s výměnou externích dat
<xref:System.Activities.Statements.Interop> Aktivita slouží ke spuštění aktivity z Windows Workflow Foundation (WF) v [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] a [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3) a pracovních postupů v rámci Windows Workflow Foundation v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4). Tento příklad ukazuje, jak nakonfigurovat a spustit WF3 pracovního postupu, který používá <xref:System.Workflow.Activities.ExternalDataExchangeService> (a odpovídající vlastní aktivity pro volání metod a zpracování událostí) s použitím <xref:System.Activities.Statements.Interop> aktivity ve službě WF4 pracovního postupu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete soubor ExternalDataExchange.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Chcete-li ukázku sestavit, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Spusťte ukázku stisknutím klávesy F5.
