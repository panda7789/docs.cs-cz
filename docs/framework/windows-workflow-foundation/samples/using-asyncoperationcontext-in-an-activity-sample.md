---
title: Pomocí AsyncOperationContext v ukázce aktivity
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: da7b62ef9e29621d1e6ee1046afb5455af1164bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a>Pomocí AsyncOperationContext v ukázce aktivity
Tento příklad ukazuje, jak vyvíjet vlastní <xref:System.Activities.CodeActivity> používající <xref:System.Activities.AsyncCodeActivityContext> pro práci asynchronně mimo pracovní postup.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Vzorová aktivita používá <xref:System.IO.FileStream.BeginWrite%2A> a <xref:System.IO.FileStream.EndWrite%2A> metody <xref:System.IO.FileStream> třída asynchronně zapsat data do souboru. Vzor sem zavedl lze upravit pro použití s jinými metodami asynchronní. Při spouštění asynchronní operaci lze provést další aktivity v pracovním postupu, ale pracovní postup nelze nastavit jako trvalý.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete Async.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavení a spuštění řešení.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`