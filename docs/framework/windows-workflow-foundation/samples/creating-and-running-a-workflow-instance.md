---
title: "Vytváření a spouštění instanci pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b25acebfaf6df68ac3163a5ef4bcb235077139cc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="creating-and-running-a-workflow-instance"></a>Vytváření a spouštění instanci pracovního postupu
Tento příklad ukazuje, jak spustit instanci pracovního postupu. Ukazuje, jak provést synchronně a asynchronně.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.  
  
## <a name="discussion"></a>Diskusní  
 První část vzorku používá <xref:System.Activities.WorkflowInvoker.Invoke%2A>. To je nejzákladnější způsob k provedení pracovního postupu. Pracovní postupy provést s <xref:System.Activities.WorkflowInvoker.Invoke%2A> jsou spouštěny synchronně.  
  
 Druhá část vzorku používá <xref:System.Activities.WorkflowApplication> třídy. <xref:System.Activities.WorkflowApplication>umožňuje mít větší kontrolu nad každou instanci, včetně možnosti pro interakci s běžícím workflowem a asynchronně spuštění pracovního postupu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a>Viz také  
 [Pomocí WorkflowInvoker a WorkflowApplication](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
