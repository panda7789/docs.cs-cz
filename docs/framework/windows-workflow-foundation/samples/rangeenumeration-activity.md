---
title: RangeEnumeration aktivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 35bff923b0e8d6fe7c01cb7970c7b6ee46488a43
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="rangeenumeration-activity"></a>RangeEnumeration aktivity
Tento příklad ukazuje, jak vytvořit vlastní aktivitu, který iteruje nad kolekcí čísel. V následující tabulce jsou hlavní soubory obsažené ve vzorku.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|RangeEnumeration.cs|Definuje vlastní aktivity s názvem `RangeEnumeration` , přepíše <xref:System.Activities.NativeActivity> třídy a smyčky prostřednictvím řady čísel.|  
|RangeEnumerationSample.cs|Klientská aplikace, která používá `RangeEnumeration` aktivity Iterujte přes kolekci čísel.|  
  
 V následující tabulce jsou vlastnosti `RangeEnumeration` aktivity.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|Spustit|Spuštění smyčky z na celé číslo.|  
|Zastavit|Zastavit smyčky v na celé číslo.|  
|Krok|Určuje, kolik k iteraci v každém.|  
|Text|Určuje kód provést při každé iteraci.|  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení RangeEnumeration.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`