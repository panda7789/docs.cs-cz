---
title: Aktivita RangeEnumeration
ms.date: 03/30/2017
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
ms.openlocfilehash: c9cf522227620422b414adc26cbc0bf338bf57d4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207587"
---
# <a name="rangeenumeration-activity"></a>Aktivita RangeEnumeration
Tento příklad ukazuje, jak vytvořit vlastní aktivitu, která iteruje přes kolekci čísel. Následující tabulka obsahuje podrobnosti o hlavních soubory zahrnuté v ukázce.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|RangeEnumeration.cs|Definuje vlastní aktivita s názvem `RangeEnumeration` , přepíše <xref:System.Activities.NativeActivity> třídy a smyčky prostřednictvím řady čísla.|  
|RangeEnumerationSample.cs|Klientské aplikace používající `RangeEnumeration` aktivity k iteraci přes kolekci čísel.|  
  
 Následující tabulka obsahuje podrobnosti o vlastnostech `RangeEnumeration` aktivity.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|Spustit|Celé číslo spustit ze smyčky.|  
|Zastavit|Celé číslo k ukončení smyčky v.|  
|Krok|Určuje, kolik k iteraci v každém.|  
|Text|Určuje kód pro spuštění při každé iteraci.|  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení RangeEnumeration.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`