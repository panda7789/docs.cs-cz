---
title: Programování stromu položek modelu
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: f2d89cb2a3b0f6167f043148ea793ec1c264a556
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038177"
---
# <a name="programming-model-item-tree"></a>Programování stromu položek modelu
Tato ukázka předvádí, <xref:System.Activities.Presentation.Model.ModelItem> jak navigovat strom pomocí deklarativní datové vazby ze zobrazení stromu Windows Presentation Foundation (WPF).

## <a name="sample-details"></a>Podrobnosti ukázky
 Strom je abstrakce, kterou používá [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastruktura k vystavování dat o upravované podkladové instanci. <xref:System.Activities.Presentation.Model.ModelItem> Následující ilustrace znázorňuje různé vrstvy infrastruktury v rámci [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].

 ![Diagram znázorňující architekturu Návrhář postupu provádění.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 Se skládá z ukazatele na podkladovou hodnotu, jakož i <xref:System.Activities.Presentation.Model.ModelProperty> kolekce objektů. <xref:System.Activities.Presentation.Model.ModelItem> Objekt je zase tvořen daty, jako jsou název a typ vlastnosti, a potom ukazatel na hodnotu, která je zase další <xref:System.Activities.Presentation.Model.ModelItem>. <xref:System.Activities.Presentation.Model.ModelProperty> Konvertor hodnot se používá k manipulaci <xref:System.Activities.Presentation.Model.ModelItem>s některými z a vrácenými z a <xref:System.Activities.Presentation.Model.ModelProperty> tak, aby se ve stromovém zobrazení zobrazovaly správně. Ukázka pak demonstruje, jak imperativně programovat <xref:System.Activities.Presentation.Model.ModelItem> proti stromu pomocí imperativní syntaxe, jak je vidět v následujícím příkladu.

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Otevřete řešení ProgrammingModelItemTree. sln v aplikaci Visual Studio 2010.

2. Sestavte řešení výběrem možnosti **Sestavit řešení** v nabídce **sestavení** .

3. Stisknutím klávesy F5 spusťte aplikaci. Pak se zobrazí formulář WPF.

4. Kliknutím na tlačítko **načíst WF** načtěte <xref:System.Activities.Presentation.Model.ModelItem> a navažte ho do stromového zobrazení.

5. Kliknutím na tlačítko **změnit strom položky modelu** se spustí předchozí kód pro přidání položky do stromu a nastavení vlastnosti.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.IValueConverter>
