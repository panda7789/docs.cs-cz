---
title: Datové vazby v klientovi Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 225bdedb67e218092ff3369d4fe742c4fc897fc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Datové vazby v klientovi Windows Presentation Foundation
Tento příklad znázorňuje použití datové vazby v klientovi Windows Presentation Foundation (WPF). Příklad používá služba Windows Communication Foundation (WCF), která generuje náhodně pole alb se vraťte do klienta. Každé album má název, ceny a seznam album sleduje. Sleduje album mít název, doba trvání. Informace, které je vrácena službou je automaticky vázána uživatelské rozhraní (UI) poskytnutý klientem Windows Presentation Foundation (WPF).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Datová vazba umožňuje zdroj dat automaticky vázat uživatelského rozhraní. To usnadňuje programovací model, protože nevyžaduje s daty z datový objekt nebo pole objektů dat prostřednictvím kódu programu aktualizovat jednotlivých prvků uživatelského rozhraní. Objekt můžete vázat na jeden element uživatelského rozhraní nebo pole do ovládacího prvku, který přebírá více vstupů, například `ListBox`. Následující kód ukazuje, jak vytvořit vazbu dat `DataContext` elementu uživatelského rozhraní.  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 V předchozí ukázce `DataContext` pro `grid` rozložení element s názvem `myPanel` je nastaven na hodnotu data vrácený `GetAlbumList` metoda. `DataContext` Umožňuje elementy dědění informace z jejich nadřazené elementy o zdroji dat, který se používá pro vazbu, jakož i dalších vlastností vazby například cestu. Pokaždé, když se aktualizuje data na serveru, je třeba spustit na řádek kódu. Například se spustí, když je inicializován okna a při přidání nové album.  
  
 V následujícím vzorovém kódu XAML `ListBox` Určuje `ItemsSource="{Binding }"`.  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 Určuje, že data vázaná na element nejvyšší úrovně uživatelského rozhraní je také vázána na tento ovládací prvek (tj. pole alb). Kromě toho `ItemTemplate="{StaticResource AlbumStyle}"` Určuje šablonu dat, který se má použít pro každou položku v `ListBox`. Můžete také definovat data šablony, které určují způsob formátování data. Těchto datových šablony můžete znovu použít pro další prvky uživatelského rozhraní v aplikaci, výhodou je, že šablona dat je definovaný a spravovaný na jednom místě.  
  
 `AlbumStyle` Datová šablona rozložen mřížky se dvěma `TextBlock`s vedle sebe. Jeden z alba Určuje název alba a jiných počet stop.  
  
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
  
 Následující kód XAML vytvoří druhý `ListBox`.  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 Určuje cestu pro kód `ItemsSource`. To znamená, že data vázaná na tento ovládací prvek není dat nejvyšší úrovně, ale vlastnost dat nejvyšší úrovně s názvem `Tracks`. Tato vlastnost představuje pole sleduje obsažené v alba. Kromě toho jiné `DataTemplate` s názvem `TrackStyle` je zadán. Rozložení `TrackStyle` šablony je podobné jako `AlbumStyle` šablony, ale `TextBlock`s jsou vázány na jiné vlastnosti. Je to proto, že se různé datové objekty se používají dvě šablony.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
  
## <a name="see-also"></a>Viz také
