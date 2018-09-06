---
title: Použití procedurálních aktivit
ms.date: 03/30/2017
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
ms.openlocfilehash: bd83f1a0fa9f3af7c22cee73fbc4f984a9ebf53c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43804748"
---
# <a name="using-procedural-activities"></a>Použití procedurálních aktivit
Ukázka používá <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, a <xref:System.Activities.Statements.WriteLine> aktivity k implementaci opakovaně uhodnout her. Náhodné číslo vybere rozluštění hry a hráč musí odhadnout toto číslo. Když hráč odešle nesprávné odhad, pracovní postup poskytuje nápovědu, jestli se má uhodnout vyšší nebo nižší. Pokud hráč uhádne číslo menší než 7 pokusů o přihlášení, zobrazí se uživateli speciální Blahopřejeme.  
  
## <a name="custom-activities-in-this-sample"></a>Vlastní aktivity v této ukázce  
  
### <a name="readline"></a>ReadLine  
 Přečte řádek textu z konzoly. Tato aktivita je odvozen od <xref:System.Activities.NativeActivity> třídy a vytvoří záložku, která je obnovit pomocí konzolové aplikace při čtení řádku.  
  
### <a name="promptint"></a>PromptInt  
 Zobrazí výzvu k zadání čísla a pak přečte z okna konzoly. Aktivita je odvozena z <xref:System.Activities.Activity%601> a používá <xref:System.Activities.Statements.WriteLine> a `ReadLine` aktivity.  
  
##### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení GuessingGame.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`