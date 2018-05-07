---
title: Obslužná rutina zrušení Compensable aktivita
ms.date: 03/30/2017
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
ms.openlocfilehash: ce4d67b26a2b4c6a9b507715b48e75e328c5b100
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cancellation-handler-on-compensable-activity"></a>Obslužná rutina zrušení Compensable aktivita
Tento příklad znázorňuje použití obslužné rutiny zrušení na <xref:System.Activities.Statements.CompensableActivity>.  
  
 Tato ukázka obsahuje dva scénáře, které ukazují použití <xref:System.Activities.Statements.CompensableActivity> zrušení. První scénář obsahuje kořenové compensable aktivity, která obsahuje tři podřízené compensable aktivit. Dva podřízené aktivity dokončit své aktivity subjekty, spouští úspěšně. Při spuštění třetí text podřízené aktivity, zaznamená výjimka, která se zpracovává souborem zrušení třetí aktivity zpracování, po jejímž uplynutí se aktivuje zrušení kořenové aktivity. Logika kořenové aktivity v tomto příkladu je odpovídajícím způsobem další dva podřízené aktivity, které dříve dokončit.  
  
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
  
 Druhý scénář znázorňuje, spuštění <xref:System.Activities.Statements.TryCatch> paralelně s <xref:System.Activities.Statements.Delay>, který končí před <xref:System.Activities.Statements.TryCatch> firemní pobočky. Je nastavena podmínka dokončení `true` po dokončení první větev způsobuje jiných větev, která má být zrušena.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete CompensationCancellation.sln.  
  
2.  Sestavit ukázku stisknutím kombinace kláves CTRL + SHIFT + B nebo vyberte možnost "Sestavit řešení" v nabídce sestavení...  
  
3.  Spustit ukázku stisknutím klávesy F5 nebo vyberte možnost "Spustit ladění" v nabídce ladění. Případně můžete stisknutím kláves Ctrl + F5 nebo vyberte možnost "Spustit bez ladění" v nabídce ladění.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`