---
title: Použití třídy WorkflowInvoker
ms.date: 03/30/2017
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
ms.openlocfilehash: d6525dbbd30aae95be4c4ee1de267736e557a541
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552202"
---
# <a name="using-the-workflowinvoker-class"></a>Použití třídy WorkflowInvoker
Tato ukázka předvádí, jak používat <xref:System.Activities.WorkflowInvoker> třídy k vyvolání aktivity, jako by šlo metodu.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Použití <xref:System.Activities.WorkflowInvoker> třída je nejjednodušší způsob, jak provést aktivitu. Je určená pro přímo spouštět aktivity, jako by šlo volání metody. Je odlehčený, vysoce výkonné, snadno použitelná rozhraní API v situacích, kde aktivity spuštění nevyžaduje infrastrukturu řízení další varianty konfigurací hostování.  
  
 Ukázka používá vlastní aktivitu, která je odvozena z <xref:System.Activities.CodeActivity%601>< Int32\> s názvem `Add` , který přidá dvě <xref:System.Activities.InArgument%601>, `X` a `Y`a vrátí `Result` <xref:System.Activities.OutArgument%601>. (<xref:System.Activities.CodeActivity%601>\<T > je odvozena z <xref:System.Activities.Activity%601>< T\>, který má <xref:System.Activities.OutArgument%601> \<T > s názvem `Result`.) A `Dictionary` \<řetězec, objekt > slouží k předávání argumentů do aktivity vyvolání prostřednictvím <xref:System.Activities.WorkflowInvoker>. Klíč slovníku odpovídá názvu argumentu na vyvolaná aktivita. Hodnota přidružená k určité klíče je vázán na argument identifikované klíčem.  
  
 Ukázka volání <xref:System.Activities.WorkflowInvoker.Invoke%2A> a předává slovník, který obsahuje hodnoty pro `X` a `Y`. <xref:System.Activities.WorkflowInvoker> Třídy váže tyto hodnoty `Add` aktivity argumenty, spustí aktivity a vrátí výsledek.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení Invoker.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte klávesu F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`