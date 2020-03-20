---
title: Programování stromu položek modelu
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f14b140fdac95f3763cc5625841a725793876fa4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142690"
---
# <a name="programming-model-item-tree"></a>Programování stromu položek modelu
Tato ukázka ukazuje, <xref:System.Activities.Presentation.Model.ModelItem> jak procházet strom pomocí deklarativní datové vazby ze stromového zobrazení Windows Presentation Foundation (WPF).

## <a name="sample-details"></a>Podrobnosti ukázky
 Strom <xref:System.Activities.Presentation.Model.ModelItem> je abstrakce, která se používá infrastruktury Windows Workflow Designer vystavit data o základní instance upravované. Následující obrázek je znázornění různých vrstev infrastruktury v rámci Návrháře pracovních postupů.

 ![Diagram, který zobrazuje architekturu Návrháře pracovních postupů.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 A <xref:System.Activities.Presentation.Model.ModelItem> se skládá z ukazatele na základní hodnotu, <xref:System.Activities.Presentation.Model.ModelProperty> stejně jako kolekce objektů. Objekt <xref:System.Activities.Presentation.Model.ModelProperty> zase skládá z dat, jako je například název a typ vlastnosti a pak ukazatel <xref:System.Activities.Presentation.Model.ModelItem>na hodnotu, která je zase jiný . Převaděč hodnot se používá k <xref:System.Activities.Presentation.Model.ModelItem>manipulaci <xref:System.Activities.Presentation.Model.ModelProperty> s některými s vrácené z a, aby se správně zobrazí ve stromovém zobrazení. Ukázka pak ukazuje, jak imperativně programovat proti stromu <xref:System.Activities.Presentation.Model.ModelItem> pomocí imperativní syntaxe, jak je vidět v následujícím příkladu.

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek

1. Otevřete řešení ProgrammingModelItemTree.sln v sadě Visual Studio 2010.

2. Vytvořte řešení výběrem **sestavení řešení** z nabídky **sestavení.**

3. Stisknutím klávesy F5 spusťte aplikaci. Poté se zobrazí formulář WPF.

4. Klepnutím na tlačítko **Načíst WF** načtěte tlačítko <xref:System.Activities.Presentation.Model.ModelItem> a spojte jej se stromovou zobrazení.

5. Kliknutím na tlačítko **Změnit strom položky modelu** se spustí předchozí kód pro přidání položky do stromu a nastavení vlastnosti.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Data.IValueConverter>
