---
title: IfElse s pravidly
ms.date: 03/30/2017
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
ms.openlocfilehash: 31906f04149a0ca7659201965ca565c7fa2af305
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483003"
---
# <a name="ifelse-with-rules"></a>IfElse s pravidly
Tento příklad ukazuje použití podmínku pravidla, která se <xref:System.Workflow.Activities.IfElseActivity> aktivity.  
  
 Ukázka předá `OrderValue` parametr z hostitele. Hodnota parametru je používán podmínku pravidla, která na první větev <xref:System.Workflow.Activities.IfElseActivity> aktivity. Pokud je hodnota menší než 10 000, provede první větev a <xref:System.Workflow.Activities.CodeActivity> aktivity v první větev vytiskne **získat schválení správcem** do konzoly. Pokud je hodnota větší než 10 000 operací, <xref:System.Workflow.Activities.CodeActivity> aktivity v druhé větvi spustí a vytiskne **získat schválení Viceprezidentka**.  
  
### <a name="to-build-the-sample"></a>K vytvoření vzorku  
  
1.  Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Spuštění řešení bez ladění stisknutím kombinace kláves CTRL + F5.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
-   V okně příkazového řádku sady SDK spusťte soubor .exe ve složce IfElseWithRules\bin\debug (nebo ve složce IfElseWithRules\bin pro verzi ukázky, která se týká jazyka Visual Basic), který se nachází pod hlavní složku pro vzorku.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
