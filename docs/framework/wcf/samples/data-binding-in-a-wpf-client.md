---
title: Datové vazby v klientovi Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 7bc389056872841905336dcf658a07223906bf82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183823"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Datové vazby v klientovi Windows Presentation Foundation
Tato ukázka ukazuje použití datové vazby v klientovi WPF (Windows Presentation Foundation). Ukázka používá službu WCF (Windows Communication Foundation), která náhodně generuje pole alb pro návrat do klienta. Každé album má název, cenu a seznam skladeb alb. Skladby alba mají název a dobu trvání. Informace vrácené službou jsou automaticky vázány na uživatelské rozhraní poskytované klientem WPF (Windows Presentation Foundation).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Datová vazba umožňuje zdroj dat automaticky vázán na ui. To zjednodušuje programovací model, protože nevyžaduje programovou aktualizaci každého prvku rozhraní s daty z datového objektu nebo pole datových objektů. Objekt můžete svázat s jedním prvkem rozhraní nebo polem s ovládacím prvkem, který přebírá více vstupů, například `ListBox`. Následující kód ukazuje, jak vázat `DataContext` data na prvek ui.  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;
}  
```  
  
 V předchozí ukázce `grid` je `myPanel` prvek `DataContext` rozložení pojmenovaný nastaven `GetAlbumList` na data vrácená metodou. Umožňuje `DataContext` prvky dědit informace z jejich nadřazené prvky o zdroj dat, který se používá pro vazbu, jakož i další charakteristiky vazby, jako je například cesta. Řádek kódu musí být proveden při každé aktualizaci dat na serveru. Například je spuštěn při inicializování okna a při přidání nového alba.  
  
 V následujícím vzorku kódu XAML `ListBox` `ItemsSource="{Binding }"`určuje .  
  
```xml  
<ListBox
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 To určuje, že data vázaná na prvek hlavní úrovně ui je také vázána na tento ovládací prvek (to znamená pole alba). Kromě toho `ItemTemplate="{StaticResource AlbumStyle}"` určuje šablonu dat, která má `ListBox`být použita pro každou položku v . Můžete také definovat šablony dat a určit způsob formátování dat. Tyto šablony dat lze znovu použít pro jiné prvky uživatelského rozhraní v aplikaci, výhodou je, že šablona dat je definována a udržována na jednom místě.  
  
 Šablona `AlbumStyle` dat obsahuje mřížku `TextBlock`se dvěma s vedle sebe. Jeden určuje název alba a druhý počet skladeb v albu.  
  
```xaml  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
```  
  
 Následující kód XAML vytvoří `ListBox`druhý .  
  
```xaml  
<ListBox Grid.Row="2"
            Grid.ColumnSpan="2"
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 Kód určuje cestu pro `ItemsSource`. To znamená, že data vázaná na tento ovládací prvek nejsou data nejvyšší `Tracks`úrovně, ale vlastnost dat nejvyšší úrovně s názvem . Tato vlastnost představuje pole skladeb obsažených v albu. Kromě toho je `DataTemplate` `TrackStyle` zadán jiný název. Rozložení `TrackStyle` šablony je podobné rozložení `AlbumStyle` šablony, ale `TextBlock`s jsou vázány na různé vlastnosti. Důvodem je, že dvě šablony se používají s různými datovými objekty.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
