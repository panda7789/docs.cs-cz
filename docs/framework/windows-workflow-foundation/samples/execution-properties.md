---
title: "Provádění vlastnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fed33544654e6929997567198c0f07346e715d1e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="execution-properties"></a>Provádění vlastnosti
Tento příklad ukazuje, jak definovat a provádění vlastnost použijte vlastní aktivity. V tomto příkladu vlastnost provádění Určuje barvu popředí v konzole. Pracovním postupu příklad ukazuje, jak různé logické cesty provádění (větví nástroje <xref:System.Activities.Statements.Parallel> aktivity) můžete udržovat různé konzoly barvy navzdory prokládaná provádění aktivity (napříč větví sady <xref:System.Activities.Statements.Parallel> aktivity).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete ExecutionProperties.sln ukázkové řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    > [!NOTE]
    >  Zobrazení ThreeColors.xaml před vytvořením řešení zobrazí chybu, protože používá vlastní aktivity musí být vytvořená ve stejnou dobu jako řešení.  
  
2.  Sestavení a spuštění řešení.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`