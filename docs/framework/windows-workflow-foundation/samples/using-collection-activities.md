---
title: Použití aktivit Collection
ms.date: 03/30/2017
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
ms.openlocfilehash: a92208583ddf1c0d5d85b5af6a250a15ac8851b9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506548"
---
# <a name="using-collection-activities"></a>Použití aktivit Collection
Tato ukázka demonstruje použití aktivit collection (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, a <xref:System.Activities.Statements.RemoveFromCollection%601>) s třídou, která implementuje <xref:System.Collections.ICollection> rozhraní a jak vytvořit vlastní aktivitu, která iteruje přes kolekci Vytiskněte obsah jednotlivých prvků v kolekci. Vlastní aktivity, který se nazývá `PrintCollection`, tiskne na konzolu členy položku kolekce s názvem `Numbers`.  
  
 Následující tabulka popisuje čtyři aktivity, které poskytují manipulaci s kolekcí pracovních postupů.  
  
|Název aktivity|Popis|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|Přidá položku do kolekce.|  
|<xref:System.Activities.Statements.ClearCollection%601>|Vymaže všechny položky v kolekci|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|Vrátí `true` Pokud zadaná položka v kolekci existuje.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|Odebere položku z kolekce.|  
  
 Vzorek se skládá ze dvou řešení, jeden v kategorii CodedWorkflow adresáře a další v adresáři DesignerWorkflow. Vysvětlují dvěma různými způsoby použití aktivity pro stejné účely.  
  
|Řešení|Popis|Hlavní soubory|  
|-|-|-|  
|CodedWorkflow|Ukázková klientská aplikace, které ukazuje, jak vyvolat aktivit collection prostřednictvím kódu programu.|**PrintCollection.cs**: aktivita pomocné rutiny vytisknout na konzole pro každou položku v kolekci.<br /><br /> **Soubor program.cs**: prostřednictvím kódu programu sestavení sekvenční aktivitu, která obsahuje řadu aktivit collection a spustí ho.|  
|DesignerWorkflow|Ukázková klientská aplikace, která demonstruje použití aktivit collection deklarativně v Návrháři pracovních postupů.|**CollectionWorkflow.xaml**: deklarativně vytvářené pomocí návrháře, který používá kolekce aktivit pracovního postupu.<br /><br /> **PrintCollection.cs**: aktivita pomocné rutiny vytisknout na konzole pro každou položku v kolekci.<br /><br /> **Soubor program.cs**: vyvolá pracovní postup popsaný v CollectionWorkflow.xaml.|  
  
 V ukázce položky členy kolekce `Numbers` jsou zobrazeny v konzole pro použití vlastní aktivity, volá `PrintCollection`.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení Collection.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`