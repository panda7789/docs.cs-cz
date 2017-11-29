---
title: Aktivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c8567eb848fbb7b5f6c68f52f1be78750a002411
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`  
  
## <a name="see-also"></a>Viz také
