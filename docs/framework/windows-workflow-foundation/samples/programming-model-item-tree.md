---
title: Programování stromu položek modelu
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: efda69ac568b0ad9c5fdcf4d42722c5b7dadd3f3
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715668"
---
# <a name="programming-model-item-tree"></a>Programování stromu položek modelu
Tato ukázka předvádí, jak navigovat <xref:System.Activities.Presentation.Model.ModelItem> stromu pomocí deklarativní datové vazby ze zobrazení stromu Windows Presentation Foundation (WPF).

## <a name="sample-details"></a>Podrobnosti ukázky
 <xref:System.Activities.Presentation.Model.ModelItem> strom je abstrakcí, kterou používá infrastruktura Windows Návrhář postupu provádění k vystavování dat o upravované podkladové instanci. Následující ilustrace znázorňuje různé vrstvy infrastruktury v rámci Návrhář postupu provádění.

 ![Diagram znázorňující architekturu Návrhář postupu provádění.](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <xref:System.Activities.Presentation.Model.ModelItem> se skládá z ukazatele na podkladovou hodnotu a kolekce objektů <xref:System.Activities.Presentation.Model.ModelProperty>. Objekt <xref:System.Activities.Presentation.Model.ModelProperty> se zase skládá z dat, jako jsou název a typ vlastnosti a potom ukazatel na hodnotu, která je zase další <xref:System.Activities.Presentation.Model.ModelItem>. Konvertor hodnot se používá k manipulaci s některými <xref:System.Activities.Presentation.Model.ModelItem>y vrácenými z <xref:System.Activities.Presentation.Model.ModelProperty>, aby byly správně zobrazeny ve stromovém zobrazení. Ukázka pak demonstruje, jak imperativně programovat do stromu <xref:System.Activities.Presentation.Model.ModelItem> pomocí imperativní syntaxe, jak je vidět v následujícím příkladu.

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

4. Kliknutím na tlačítko **Load WF** načtěte <xref:System.Activities.Presentation.Model.ModelItem> a vytvořte jeho svázání se stromovým zobrazením.

5. Kliknutím na tlačítko **změnit strom položky modelu** se spustí předchozí kód pro přidání položky do stromu a nastavení vlastnosti.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.IValueConverter>
