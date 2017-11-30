---
title: "Pomocí AsyncOperationContext v ukázce aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ae62192517ee9117092ff11d2da5212d5a1c1fff
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`