---
title: Datové vazby v klientovi Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 1bc6dd2ef981115068cbd4cd491a14fea70d7e3a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979859"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Datové vazby v klientovi Windows Presentation Foundation
Tento příklad ukazuje použití datové vazby v klientovi Windows Presentation Foundation (WPF). Ukázka používá služba Windows Communication Foundation (WCF), která náhodně generovat pole alb vrácena klientovi. Každé album má název, cenu a seznam alba stopy. Sleduje alba mají název a doba trvání. Informace, které je vrácena službou je automaticky vázán na uživatelské rozhraní (UI) poskytuje klientovi Windows Presentation Foundation (WPF).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Datová vazba umožňuje zdroj dat se automaticky svázán s uživatelským rozhraním. To usnadňuje programovací model, protože nevyžaduje programově aktualizovat každého prvku uživatelského rozhraní pomocí dat z datového objektu nebo pole datových objektů. Objekt můžete vázat na jeden prvek uživatelského rozhraní nebo pole do ovládacího prvku, který přijímá více vstupů, například `ListBox`. Následující kód ukazuje, jak vytvořit vazbu dat `DataContext` prvku uživatelského rozhraní.  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 V předchozí ukázce `DataContext` pro `grid` rozložení element s názvem `myPanel` nastavená na dat vrácených `GetAlbumList` metoda. `DataContext` Umožňuje prvkům dědit informace jejich nadřazených prvků o zdroji dat, který se používá pro vazbu, stejně jako ostatní vlastnosti vazby, jako je například cesta. Pokaždé, když se aktualizuje data na serveru, je třeba spustit na řádek kódu. Například se provede při inicializaci okna a když se přidá nový obrázek.  
  
 V následujícím ukázkovém kódu XAML `ListBox` Určuje `ItemsSource="{Binding }"`.  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 Určuje, že data vázaná na element nejvyšší úrovně uživatelského rozhraní je dále vázané na tento ovládací prvek (tedy pole alb). Kromě toho `ItemTemplate="{StaticResource AlbumStyle}"` Určuje šablonu, data se použije pro každou položku v `ListBox`. Můžete také definovat data šablony, které určují způsob formátování data. Tyto údaje, které šablony lze znovu použít pro ostatní prvky uživatelského rozhraní v aplikaci, výhodou je, že šablony je definovaný a spravovaný na jednom místě.  
  
 `AlbumStyle` Šablona rozložen mřížky se dvěma `TextBlock`s vedle sebe. Jeden alba Určuje název alba a jiných počet stop.  
  
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
  
 Následující kód XAML vytvoří druhou `ListBox`.  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 Určuje cestu pro kód `ItemsSource`. To znamená, že data vázaná na tento ovládací prvek není dat nejvyšší úrovně, ale vlastnost dat nejvyšší úrovně s názvem `Tracks`. Tato vlastnost představuje pole obsažené v alba sleduje. Kromě toho jiný `DataTemplate` s názvem `TrackStyle` určena. Rozložení `TrackStyle` šablona je podobná `AlbumStyle` šablony, ale `TextBlock`s jsou vázány na jiné vlastnosti. Je to proto, že tyto dvě šablony se používají s různými datovými objekty.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
