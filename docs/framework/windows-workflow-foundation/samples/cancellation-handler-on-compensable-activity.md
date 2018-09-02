---
title: Obslužná rutina zrušení u Kompenzovatelné aktivity
ms.date: 03/30/2017
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
ms.openlocfilehash: 2f32d10e22be7fdd1e84229a214409df06efa918
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442704"
---
# <a name="cancellation-handler-on-compensable-activity"></a>Obslužná rutina zrušení u Kompenzovatelné aktivity
Tato ukázka demonstruje použití obslužná rutina zrušení na <xref:System.Activities.Statements.CompensableActivity>.  
  
 Tato ukázka obsahuje dva scénáře, které ukazují použití <xref:System.Activities.Statements.CompensableActivity> zrušení. První scénář obsahuje kořenový kompenzovatelná aktivita, která obsahuje tři podřízené kompenzovatelné aktivity. Dvě podřízené aktivity dokončení úřadů, které jejich činnost úspěšně. Třetí text podřízené aktivity spustí, zjistí výjimku, která zpracovává zrušení třetí aktivity zpracování, po jejímž uplynutí se aktivuje zrušení kořenovou aktivitu. Logika v kořenové aktivity v tomto příkladu je odpovídajícím způsobem upravit další dva podřízené aktivity, která dokončila dříve.  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 Druhý scénář předvádí, provádění <xref:System.Activities.Statements.TryCatch> souběžně s <xref:System.Activities.Statements.Delay>, který končí před <xref:System.Activities.Statements.TryCatch> větve. Je nastavena podmínka ukončení `true` po dokončení první větev, příčinou této větve zrušit.  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete CompensationCancellation.sln.  
  
2.  Sestavit ukázku stisknutím kombinace kláves CTRL + SHIFT + B nebo vyberte "Sestavit řešení" v nabídce sestavení...  
  
3.  Spusťte ukázku stisknutím klávesy F5 nebo vyberte "Spustit ladění" z menu ladit. Případně můžete stisknutím kláves Ctrl + F5 nebo vyberte možnost "Spustit bez ladění" z menu ladit.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`