---
title: 'Postupy: Vytvoření a připojení ke kolekci ObservableCollection'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], ObservableCollection class
- notifications [WPF]
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
ms.openlocfilehash: 5e04aa1a1d209074dbdadcb1df089e31efa84ded
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556715"
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a>Postupy: Vytvoření a připojení ke kolekci ObservableCollection
Tento příklad ukazuje, jak vytvořit a vytvořit vazbu na kolekce, která je odvozena z <xref:System.Collections.ObjectModel.ObservableCollection%601> třídy, která je třída kolekce, která poskytuje oznámení, pokud získat položky přidány nebo odebrány.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, provádění `NameList` kolekce:  
  
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
  
 Můžete zpřístupnit kolekce pro vazby stejně jako kdybyste s jinými [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekty, jak je popsáno v [zkontrolujte Data k dispozici pro vazbu v jazyce XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md). Například můžete vytvořit instanci kolekce v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a určete kolekci jako prostředek, jak je vidět tady:  
  
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
  
 Potom můžete vázat na kolekci:  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 Definice `NameItemTemplate` není zobrazeny zde.  
  
> [!NOTE]
>  Objekty v kolekci musí splňovat požadavky popsané v [vazby Přehled zdrojů](../../../../docs/framework/wpf/data/binding-sources-overview.md). Konkrétně, pokud používáte <xref:System.Windows.Data.BindingMode.OneWay> nebo <xref:System.Windows.Data.BindingMode.TwoWay> (například chcete vaší [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aktualizovat při změně vlastnosti zdroje dynamicky), je nutné implementovat změněné vlastnosti vhodný mechanismus oznámení například <xref:System.ComponentModel.INotifyPropertyChanged>rozhraní.  
  
 Další informace najdete v tématu vazby v části kolekce [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Řazení dat v zobrazení](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [Filtrování dat v zobrazení](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [Řazení a seskupení dat pomocí zobrazení XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
