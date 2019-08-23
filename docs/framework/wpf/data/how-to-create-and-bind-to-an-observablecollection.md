---
title: 'Postupy: Vytvoření a vytvoření vazby ke kolekci ObservableCollection'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], ObservableCollection class
- notifications [WPF]
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
ms.openlocfilehash: 8db9f2051a0401e01f233f9c959e015eb657bdac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965467"
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a>Postupy: Vytvoření a vytvoření vazby ke kolekci ObservableCollection
Tento příklad ukazuje, jak vytvořit a vytvořit vazby na kolekci, která je odvozena <xref:System.Collections.ObjectModel.ObservableCollection%601> z třídy, což je třída kolekce, která poskytuje oznámení, když se položky přidají nebo odeberou.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci `NameList` kolekce:  
  
```csharp  
public class NameList : ObservableCollection<PersonName>  
{  
    public NameList() : base()  
    {  
        Add(new PersonName("Willa", "Cather"));  
        Add(new PersonName("Isak", "Dinesen"));  
        Add(new PersonName("Victor", "Hugo"));  
        Add(new PersonName("Jules", "Verne"));  
    }  
  }  
  
  public class PersonName  
  {  
      private string firstName;  
      private string lastName;  
  
      public PersonName(string first, string last)  
      {  
          this.firstName = first;  
          this.lastName = last;  
      }  
  
      public string FirstName  
      {  
          get { return firstName; }  
          set { firstName = value; }  
      }  
  
      public string LastName  
      {  
          get { return lastName; }  
          set { lastName = value; }  
      }  
  }  
```  
  
```vb  
Public Class NameList  
    Inherits ObservableCollection(Of PersonName)  
  
    ' Methods  
    Public Sub New()  
        MyBase.Add(New PersonName("Willa", "Cather"))  
        MyBase.Add(New PersonName("Isak", "Dinesen"))  
        MyBase.Add(New PersonName("Victor", "Hugo"))  
        MyBase.Add(New PersonName("Jules", "Verne"))  
    End Sub  
  
End Class  
  
Public Class PersonName  
    ' Methods  
    Public Sub New(ByVal first As String, ByVal last As String)  
        Me._firstName = first  
        Me._lastName = last  
    End Sub  
  
    ' Properties  
    Public Property FirstName() As String  
        Get  
            Return Me._firstName  
        End Get  
        Set(ByVal value As String)  
            Me._firstName = value  
        End Set  
    End Property  
  
    Public Property LastName() As String  
        Get  
            Return Me._lastName  
        End Get  
        Set(ByVal value As String)  
            Me._lastName = value  
        End Set  
    End Property  
  
    ' Fields  
    Private _firstName As String  
    Private _lastName As String  
End Class  
```  
  
 Kolekci lze vytvořit pro vazbu stejným způsobem jako ostatní objekty modulu CLR (Common Language Runtime), jak je popsáno v tématu [zpřístupnění dat pro vazbu v jazyce XAML](how-to-make-data-available-for-binding-in-xaml.md). Například můžete vytvořit instanci kolekce v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a zadat kolekci jako prostředek, jak je znázorněno zde:  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:c="clr-namespace:SDKSample"  
  x:Class="SDKSample.Window1"  
  Width="400"  
  Height="280"  
  Title="MultiBinding Sample">  
  
  <Window.Resources>  
    <c:NameList x:Key="NameListData"/>  
  
...  
  
</Window.Resources>  
```  
  
 Pak můžete vytvořit vazby na kolekci:  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 Tady není zobrazená definice `NameItemTemplate` .  
  
> [!NOTE]
> Objekty v kolekci musí splňovat požadavky popsané v tématu [Přehled zdrojů vazby](binding-sources-overview.md). Zejména pokud používáte <xref:System.Windows.Data.BindingMode.OneWay> nebo <xref:System.Windows.Data.BindingMode.TwoWay> ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] například chcete, aby se aktualizace aktualizovaly, když se dynamicky mění vlastnosti zdrojového kódu), musíte implementovat vhodný mechanizmus oznámení změněné vlastnosti, jako je například <xref:System.ComponentModel.INotifyPropertyChanged>rozhraní.  
  
 Další informace najdete v části vazba na kolekce v tématu [Přehled datové vazby](data-binding-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Řazení dat v zobrazení](how-to-sort-data-in-a-view.md)
- [Filtrování dat v zobrazení](how-to-filter-data-in-a-view.md)
- [Řazení a seskupení dat pomocí zobrazení XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
