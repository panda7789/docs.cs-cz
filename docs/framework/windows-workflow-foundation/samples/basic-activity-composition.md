---
title: "Složení základní aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f1c94a276cf2e76d595a22c5c930614818bbf2b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="basic-activity-composition"></a>Složení základní aktivity
Tato ukázka ukazuje, jak vytvořit vlastní aktivity a poskytované systémem aktivit vytvořit více vlastních aktivit.  
  
 Pracovní postup pomocí aktivity průzkum plány průzkum seznam otázky a poté uloží odpovědí přijatých.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Tato ukázka používá tři vlastní aktivity. `ReadLine`je jednoduchý <xref:System.Activities.NativeActivity> \<řetězec > vytvářející <xref:System.Activities.Bookmark> při naplánované a nastaví `Return` <xref:System.Activities.OutArgument%601> na hodnotu, se kterým <xref:System.Activities.Bookmark> obnovení. `Prompt`je <xref:System.Activities.Activity%601> \<řetězec >, která má <xref:System.Activities.InArgument%601>< řetězec\> s názvem `Text` a vrátí uživatele v odpovědi `Result` <xref:System.Activities.OutArgument%601> \<řetězec >. `Prompt` Používá aktivitu <xref:System.Activities.Statements.Sequence> a <xref:System.Activities.Statements.WriteLine> aktivity, které se dodávají jako součást rozhraní .NET Framework a zahrnuje také vlastní `ReadLine` aktivity pro získání vstupu uživatele. Poslední vlastní aktivita tvoří `Survey` aktivity. Je <xref:System.Activities.Activity>< ICollection\<řetězec >>.  Tato aktivita přijímá <xref:System.Activities.InArgument%601>< IEnumerable < řetězec\>> s názvem `Questions` a naplní `Result` out argument s odpovědí. `Survey` Aktivita používá <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> a <xref:System.Activities.Statements.AddToCollection%601> z rozhraní .NET Framework a zahrnuje `Prompt` aktivity pro otázkami průzkum a získávání odpovědí.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete **BasicActivityComposition.sln** ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavení a spuštění řešení.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`  
  
## <a name="see-also"></a>Viz také
