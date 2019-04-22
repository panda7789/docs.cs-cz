---
title: Programování stromu položek modelu
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 1aaa1aa9922a7f57138782effe9492ec84198c8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771605"
---
# <a name="programming-model-item-tree"></a>Programování stromu položek modelu
Tato ukázka předvádí, jak přejít <xref:System.Activities.Presentation.Model.ModelItem> stromové struktury pomocí deklarativní datové vazby ve stromovém zobrazení Windows Presentation Foundation (WPF).

## <a name="sample-details"></a>Ukázka podrobnosti
 <xref:System.Activities.Presentation.Model.ModelItem> Stromu je úrovní abstrakce, jakou používají [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastruktury ke zveřejňování dat o základní instance, který právě upravujete. Na následujícím obrázku je znázornění různé vrstvy v rámci infrastruktury [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].

 ![Diagram znázorňující architekturu návrháře postupu provádění.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 A <xref:System.Activities.Presentation.Model.ModelItem> se skládá z ukazatele na základní hodnotu, stejně jako kolekce <xref:System.Activities.Presentation.Model.ModelProperty> objekty. A <xref:System.Activities.Presentation.Model.ModelProperty> objekt zase obsahuje data, jako jsou název a typ vlastnosti a pak ukazatel na hodnotu, která je dále jiného <xref:System.Activities.Presentation.Model.ModelItem>. Převaděč hodnoty se používá k manipulaci s některé <xref:System.Activities.Presentation.Model.ModelItem>s vrácená <xref:System.Activities.Presentation.Model.ModelProperty> tak, aby byly správně zobrazí ve stromovém zobrazení. Ukázka pak ukazuje, jak toho programovat proti <xref:System.Activities.Presentation.Model.ModelItem> stromu pomocí imperativní syntaxe, jak je znázorněno v následujícím příkladu.

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1. Otevřete ProgrammingModelItemTree.sln řešení v sadě Visual Studio 2010.

2. Sestavte řešení tak, že vyberete **sestavit řešení** z **sestavení** nabídky.

3. Stisknutím klávesy F5 spusťte aplikaci. [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] Se pak zobrazí formulář.

4. Klikněte na tlačítko **načíst WF** tlačítko načtete <xref:System.Activities.Presentation.Model.ModelItem> a jeho vazbu na stromové zobrazení.

5. Kliknutím **změnit Model položka stromu** tlačítko spustí předchozí kód pro přidání položky do stromu a nastavení vlastnosti.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.IValueConverter>
