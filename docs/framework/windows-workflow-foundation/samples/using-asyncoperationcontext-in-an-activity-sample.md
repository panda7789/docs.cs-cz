---
title: Použití AsyncOperationContext v ukázce aktivity
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: 4358a364a3f7ec69b7c1c548fcf82fe494f37505
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078896"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a>Použití AsyncOperationContext v ukázce aktivity
Tato ukázka předvádí, jak vyvíjet vlastní <xref:System.Activities.CodeActivity> , která používá <xref:System.Activities.AsyncCodeActivityContext> a provádí práci asynchronně mimo pracovní postup.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Vzorová aktivita používá <xref:System.IO.FileStream.BeginWrite%2A> a <xref:System.IO.FileStream.EndWrite%2A> metody <xref:System.IO.FileStream> třídy asynchronního zápisu dat do souboru. Vzor zavedené zde lze upravit pomocí jiné asynchronní metody. Při provádění asynchronní operace, můžete provést další aktivity v pracovním postupu, ale pracovní postup nelze nastavit jako trvalý.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Otevřete v ukázkovém řešení Async.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte a spusťte řešení.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`