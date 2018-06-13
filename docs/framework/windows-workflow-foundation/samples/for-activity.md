---
title: Aktivity
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: c79f295e7880f845c606a55f9c56ad65350f9c52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515442"
---
# <a name="for-activity"></a>Aktivity
Ukázka For ukazuje, jak vytvářet vlastní aktivity, která dědí z <xref:System.Activities.NativeActivity>a použít ho v pracovní postup provést v reálném světě příkladu. Vlastní aktivity obsažené v této ukázkové funkce jako jazyka C# `for` příkaz. T  
  
 `For` Vlastní aktivita má vlastností s názvem `InitAction`, `IterationAction`, `Condition`, a `Body` , odpovídají inicializace příkaz, příkaz iterativní, pokračování podmínku a textu v uvedeném pořadí – příkaz najít v standardní jazyka C# `For` příkaz.  
  
 Následující tabulka popisuje soubory klíčů ve vzorku.  
  
|Soubor|Popis|  
|----------|-----------------|  
|For.cs|Definice pro třídy `For` vlastní aktivitu, která rozšiřuje <xref:System.Activities.NativeActivity> třída poskytuje funkce jazyka C# `For` příkaz.|  
|Program.cs|Klientská aplikace, která provádí základní iterativní práci na kolekci pomocí vlastní `For` aktivity.|  
  
> [!NOTE]
>  Při použití `For` vlastní aktivitu, ujistěte se, že `Condition` je nastavena; jinak může dojít k nekonečné smyčce.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vytvořit vlastní aktivitu, která dědí z <xref:System.Activities.NativeActivity>.  
  
## <a name="discussion"></a>Diskusní  
 Následující tabulka popisuje vlastnosti aktivity obsažené v této ukázce.  
  
 InitAction  
 Inicializace – příkaz  
  
 IterationAction  
 Iterační – příkaz  
  
 Podmínka  
 Pokračování – příkaz  
  
 Text  
 Text – příkaz  
  
 Aktivity dědí z <xref:System.Activities.NativeActivity> k získání přístupu k funkcím runtime například plánování další aktivity byste měli spustit, pomocí jedné z `ScheduleActivity` metody <xref:System.Activities.NativeActivityContext>.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení For.sln.  
  
2.  Sestavte řešení, stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Stisknutím klávesy F5 spusťte tohoto řešení.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`