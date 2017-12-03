---
title: "Omezenému paralelní ForEach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d7a3ea5f4ec911a6965ce07c098d460ca0cbd929
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="throttled-parallel-foreach"></a>Omezenému paralelní ForEach
`ThrottleParallelForEach` Aktivity je podobná <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` aktivity s jednou výjimkou to umožňuje nastavení souběžnosti Multi-Factor omezit počet souběžných větví provést. `ThrottleParallelForEach` Aktivity je odvozena z <xref:System.Activities.NativeActivity>, protože je nutné ho naplánovat další aktivity (podřízené aktivity) a používá se pouze přístupné prostřednictvím <xref:System.Activities.NativeActivityContext> třídy.  
  
## <a name="projects"></a>Projekty  
  
|**Název projektu**|**Popis**|**Hlavní soubory**|  
|-|-|-|  
|ThrottledParallelForEach|Obsahuje `ThrottledParallelForEach` aktivita a její designer.|ThrottledParallelForEach.cs<br /><br /> `ThrottledParallelForEach` Definici aktivity.|  
|CodeTestClient|Ukázková aplikace klienta, která slouží ke konfiguraci a spuštění pracovního postupu s `ThrottledParallelForEach` pomocí imperativní kódu.|Program.cs<br /><br /> Definuje a spouští instanci ukázkový pracovní postup.|  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor ThrottledParallelForEach.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`