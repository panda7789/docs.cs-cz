---
title: "Pomocí procedurální aktivit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6516f5da83a4133451d73fc10a76a691a931d3ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-procedural-activities"></a>Pomocí procedurální aktivit
Ukázce se používá <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, a <xref:System.Activities.Statements.WriteLine> aktivity k implementaci uhodnutí her. Hádání herní vybere náhodné číslo a má přehrávač tak snadno uhodnout toto číslo. Když přehrávač odešle nesprávné odhad, pracovní postup poskytuje nápovědu ohledně uhodnout vyšší nebo nižší. Pokud přehrávač odhadne číslo menší než 7 pokusů o přihlášení, zobrazí se uživateli speciální Blahopřejeme.  
  
## <a name="custom-activities-in-this-sample"></a>Vlastní aktivity v této ukázce  
  
### <a name="readline"></a>ReadLine  
 Přečte řádek textu z konzoly. Tato aktivita je odvozena z <xref:System.Activities.NativeActivity> třídy a vytvoří záložku, na kterou je obnoveno pomocí konzolové aplikace, pokud je pro čtení na řádku.  
  
### <a name="promptint"></a>PromptInt  
 Zobrazí výzvu k zadání čísla a potom načte z okna konzoly. Aktivita je odvozena z <xref:System.Activities.Activity%601> a používá <xref:System.Activities.Statements.WriteLine> a `ReadLine` aktivity.  
  
##### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení GuessingGame.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`