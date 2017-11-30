---
title: "Používání třídy WorkflowInvoker"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8bb6c4049b56702c8fad226c20884ff581ec6203
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-workflowinvoker-class"></a>Používání třídy WorkflowInvoker
Tento příklad znázorňuje způsob použití <xref:System.Activities.WorkflowInvoker> třída má být vyvolán aktivity, jako by šlo metodu.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Pomocí <xref:System.Activities.WorkflowInvoker> třída je nejjednodušší způsob, jak provést aktivitu. Je určený pro přímo spouštět aktivitu, jako by šlo volání metody. Je jednoduché, vysoce výkonné, snadno použitelné rozhraní API v situacích, kde provádění aktivity nevyžaduje infrastrukturu řízení jiných hostitelských variace.  
  
 Ukázka používá vlastní aktivity, která je odvozena z <xref:System.Activities.CodeActivity%601>< Int32\> s názvem `Add` , přidá dva <xref:System.Activities.InArgument%601>, `X` a `Y`a vrátí `Result` <xref:System.Activities.OutArgument%601>. (<xref:System.Activities.CodeActivity%601>\<T > je odvozena z <xref:System.Activities.Activity%601>< T\>, který má <xref:System.Activities.OutArgument%601> \<T > s názvem `Result`.) A `Dictionary` \<řetězec, objekt > slouží k předání argumentů do aktivity vyvolání prostřednictvím <xref:System.Activities.WorkflowInvoker>. Klíče slovníku odpovídá názvu argument vyvolaná aktivita. Hodnoty přidružené k určité klíči je vázána k argumentu identifikovat pomocí klíče.  
  
 Ukázka volání <xref:System.Activities.WorkflowInvoker.Invoke%2A> a předá slovník, který obsahuje hodnoty pro `X` a `Y`. <xref:System.Activities.WorkflowInvoker> Třída váže tyto hodnoty `Add` aktivity je argumenty, provádí aktivity a vrátí výsledek.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení Invoker.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`