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
# <a name="how-to-create-and-bind-to-an-observablecollection"></a><span data-ttu-id="158c4-102">Postupy: Vytvoření a vytvoření vazby ke kolekci ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="158c4-102">How to: Create and Bind to an ObservableCollection</span></span>
<span data-ttu-id="158c4-103">Tento příklad ukazuje, jak vytvořit a vytvořit vazby na kolekci, která je odvozena <xref:System.Collections.ObjectModel.ObservableCollection%601> z třídy, což je třída kolekce, která poskytuje oznámení, když se položky přidají nebo odeberou.</span><span class="sxs-lookup"><span data-stu-id="158c4-103">This example shows how to create and bind to a collection that derives from the <xref:System.Collections.ObjectModel.ObservableCollection%601> class, which is a collection class that provides notifications when items get added or removed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="158c4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="158c4-104">Example</span></span>  
 <span data-ttu-id="158c4-105">Následující příklad ukazuje implementaci `NameList` kolekce:</span><span class="sxs-lookup"><span data-stu-id="158c4-105">The following example shows the implementation of a `NameList` collection:</span></span>  
  
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
  
 <span data-ttu-id="158c4-106">Kolekci lze vytvořit pro vazbu stejným způsobem jako ostatní objekty modulu CLR (Common Language Runtime), jak je popsáno v tématu [zpřístupnění dat pro vazbu v jazyce XAML](how-to-make-data-available-for-binding-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="158c4-106">You can make the collection available for binding the same way you would with other common language runtime (CLR) objects, as described in [Make Data Available for Binding in XAML](how-to-make-data-available-for-binding-in-xaml.md).</span></span> <span data-ttu-id="158c4-107">Například můžete vytvořit instanci kolekce v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a zadat kolekci jako prostředek, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="158c4-107">For example, you can instantiate the collection in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and specify the collection as a resource, as shown here:</span></span>  
  
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
  
 <span data-ttu-id="158c4-108">Pak můžete vytvořit vazby na kolekci:</span><span class="sxs-lookup"><span data-stu-id="158c4-108">You can then bind to the collection:</span></span>  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 <span data-ttu-id="158c4-109">Tady není zobrazená definice `NameItemTemplate` .</span><span class="sxs-lookup"><span data-stu-id="158c4-109">The definition of `NameItemTemplate` is not shown here.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="158c4-110">Objekty v kolekci musí splňovat požadavky popsané v tématu [Přehled zdrojů vazby](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="158c4-110">The objects in your collection must satisfy the requirements described in the [Binding Sources Overview](binding-sources-overview.md).</span></span> <span data-ttu-id="158c4-111">Zejména pokud používáte <xref:System.Windows.Data.BindingMode.OneWay> nebo <xref:System.Windows.Data.BindingMode.TwoWay> ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] například chcete, aby se aktualizace aktualizovaly, když se dynamicky mění vlastnosti zdrojového kódu), musíte implementovat vhodný mechanizmus oznámení změněné vlastnosti, jako je například <xref:System.ComponentModel.INotifyPropertyChanged>rozhraní.</span><span class="sxs-lookup"><span data-stu-id="158c4-111">In particular, if you are using <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> (for example, you want your [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to update when the source properties change dynamically), you must implement a suitable property changed notification mechanism such as the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span>  
  
 <span data-ttu-id="158c4-112">Další informace najdete v části vazba na kolekce v tématu [Přehled datové vazby](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="158c4-112">For more information, see the Binding to Collections section in the [Data Binding Overview](data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="158c4-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="158c4-113">See also</span></span>

- [<span data-ttu-id="158c4-114">Řazení dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="158c4-114">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="158c4-115">Filtrování dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="158c4-115">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="158c4-116">Řazení a seskupení dat pomocí zobrazení XAML</span><span class="sxs-lookup"><span data-stu-id="158c4-116">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="158c4-117">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="158c4-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="158c4-118">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="158c4-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
