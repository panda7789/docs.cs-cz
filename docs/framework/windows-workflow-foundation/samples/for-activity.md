---
title: Pro aktivitu
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: 7a7023abb9057ab4b25552fbf9a81cd2ae2b4e88
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801843"
---
# <a name="for-activity"></a>Pro aktivitu
Ukázka pro předvádí, jak vytvořit vlastní aktivitu, která dědí z <xref:System.Activities.NativeActivity>a použít ho v pracovním postupu spustit příklad reálného světa. Vlastní aktivity, které jsou zahrnuté v této ukázkové funkce, jako je C# `for` příkazu. T  
  
 `For` Vlastní aktivita má vlastnosti s názvem `InitAction`, `IterationAction`, `Condition`, a `Body` , které odpovídají příkaz inicializace, iterativního příkazu, pokračování podmínku a těla příkazu v uvedeném pořadí součástí standard jazyka C# `For` příkazu.  
  
 Následující tabulka popisuje soubory klíčů ve vzorku.  
  
|Soubor|Popis|  
|----------|-----------------|  
|For.cs|Třídy definice `For` vlastní aktivitu, která rozšiřuje <xref:System.Activities.NativeActivity> třídy pro zajištění funkcí jazyka C# `For` příkazu.|  
|Program.cs|Klientská aplikace, který provádí základní iterativní práci na kolekci pomocí vlastní `For` aktivity.|  
  
> [!NOTE]
>  Při použití `For` vlastní aktivitu, ujistěte se, že `Condition` je nastavena; jinak může dojít k nekonečné smyčce.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vytvořit vlastní aktivitu, která dědí z <xref:System.Activities.NativeActivity>.  
  
## <a name="discussion"></a>Diskuse  
 Následující tabulka popisuje vlastnosti aktivity zahrnuté v této ukázce.  
  
 InitAction  
 Inicializace – příkaz  
  
 IterationAction  
 Iterativní – příkaz  
  
 Podmínka  
 Příkaz pokračování  
  
 Text  
 Text příkazu  
  
 Aktivita dědí z <xref:System.Activities.NativeActivity> k získání přístupu k vlastnosti modulu runtime, jako je plánování další aktivity byste měli spustit, použijte některý `ScheduleActivity` metody <xref:System.Activities.NativeActivityContext>.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení For.sln.  
  
2.  Sestavte řešení, stisknutím kombinace kláves CTRL + SHIFT + B.  
  
3.  Spuštění řešení, stisknutím klávesy F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`