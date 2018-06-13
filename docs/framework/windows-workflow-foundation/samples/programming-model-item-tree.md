---
title: Programování modelu položka stromu
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: c5bbbba4f599801c5bffdbd19e14295ff239dfcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516471"
---
# <a name="programming-model-item-tree"></a>Programování modelu položka stromu
Tento příklad znázorňuje, jak se orientovat <xref:System.Activities.Presentation.Model.ModelItem> stromu pomocí deklarativní data vazby z Windows Presentation Foundation (WPF) stromovém zobrazení.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 <xref:System.Activities.Presentation.Model.ModelItem> Stromu je abstrakce, který je používán [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastruktury vystavit data o základní instanci Upravovaný. Na následujícím obrázku je popis shromažďování různé vrstvy v rámci infrastruktury [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].  
  
 ![Architektura Návrháře pracovního postupu](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")  
  
 A <xref:System.Activities.Presentation.Model.ModelItem> se skládá z ukazatel na základní hodnotu, stejně jako kolekce <xref:System.Activities.Presentation.Model.ModelProperty> objekty. A <xref:System.Activities.Presentation.Model.ModelProperty> objekt zase obsahuje data, jako jsou název a typ vlastnosti a pak ukazatel na hodnotu, která je jiné zase, <xref:System.Activities.Presentation.Model.ModelItem>. Převaděč hodnoty se používá k manipulaci s některé <xref:System.Activities.Presentation.Model.ModelItem>s vrácených <xref:System.Activities.Presentation.Model.ModelProperty> tak, aby byly správně objeví ve stromovém zobrazení. Ukázka pak ukazuje, jak imperativní programu proti <xref:System.Activities.Presentation.Model.ModelItem> stromu pomocí imperativní syntaxe, jak je vidět v následujícím příkladu.  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení ProgrammingModelItemTree.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení výběrem **sestavit řešení** z **sestavení** nabídky.  
  
3.  Stisknutím klávesy F5 spusťte aplikaci. [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] Se následně zobrazí formulář.  
  
4.  Klikněte na tlačítko **načíst WF** tlačítko Načíst <xref:System.Activities.Presentation.Model.ModelItem> a navázat jej stromovém zobrazení.  
  
5.  Kliknutím **změn modelu položka stromu** tlačítko spustí předchozí kód k přidání položky do stromu a nastavte vlastnost.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Data.IValueConverter>
