---
title: 'Postupy: Řazení sloupce GridView při kliknutí na záhlaví'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], GridView
- controls [WPF], ListView
- ListView controls [WPF], sorting GridView columns
- GridView controls [WPF], ListView control
ms.assetid: 4865d720-d147-40ed-83a7-af7587f8aad8
ms.openlocfilehash: 3438ab91045a144a7fa1d531e9d7d55ad30e89ea
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57844285"
---
# <a name="how-to-sort-a-gridview-column-when-a-header-is-clicked"></a>Postupy: Řazení sloupce GridView při kliknutí na záhlaví

Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.ListView> ovládací prvek, který implementuje <xref:System.Windows.Controls.GridView> zobrazit režimu a seřadí data obsahu, když uživatel klikne na záhlaví sloupce.

## <a name="example"></a>Příklad

Následující příklad definuje <xref:System.Windows.Controls.GridView> se třemi sloupci, kteří jsou navázáni na <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, a <xref:System.DateTime.Day%2A>, vlastnosti <xref:System.DateTime> struktury.

```xaml
<GridView>
  <GridViewColumn DisplayMemberBinding="{Binding Path=Year}"
                  Header="Year"
                  Width="100"/>
  <GridViewColumn DisplayMemberBinding="{Binding Path=Month}"
                  Header="Month"
                  Width="100"/>
  <GridViewColumn DisplayMemberBinding="{Binding Path=Day}"
                  Header="Day"
                  Width="100"/>
</GridView>
```

Následující příklad ukazuje datové položky, které jsou definovány jako <xref:System.Collections.ArrayList> z <xref:System.DateTime> objekty. <xref:System.Collections.ArrayList> Je definován jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> pro <xref:System.Windows.Controls.ListView> ovládacího prvku.

```xaml
<ListView.ItemsSource>
  <s:ArrayList>
    <p:DateTime>1993/1/1 12:22:02</p:DateTime>
    <p:DateTime>1993/1/2 13:2:01</p:DateTime>
    <p:DateTime>1997/1/3 2:1:6</p:DateTime>
    <p:DateTime>1997/1/4 13:6:55</p:DateTime>
    <p:DateTime>1999/2/1 12:22:02</p:DateTime>
    <p:DateTime>1998/2/2 13:2:01</p:DateTime>
    <p:DateTime>2000/2/3 2:1:6</p:DateTime>
    <p:DateTime>2002/2/4 13:6:55</p:DateTime>
    <p:DateTime>2001/3/1 12:22:02</p:DateTime>
    <p:DateTime>2006/3/2 13:2:01</p:DateTime>
    <p:DateTime>2004/3/3 2:1:6</p:DateTime>
    <p:DateTime>2004/3/4 13:6:55</p:DateTime>
  </s:ArrayList>
</ListView.ItemsSource>
```

`s` a `p` identifikátory v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] značek najdete mapování oboru názvů, které jsou definované v metadatech [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky. Následující příklad ukazuje definici metadat.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="ListViewSort.Window1"
    xmlns:s="clr-namespace:System.Collections;assembly=mscorlib"
    xmlns:p="clr-namespace:System;assembly=mscorlib">
```

Řazení dat podle obsahu sloupce, příklad definuje obslužnou rutinu události pro zpracování <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, která nastane po stisknutí tlačítka záhlaví sloupce. Následující příklad ukazuje, jak určit obslužnou rutinu události pro <xref:System.Windows.Controls.GridViewColumnHeader> ovládacího prvku.

```xaml
<ListView x:Name='lv' Height="150" HorizontalAlignment="Center"
  VerticalAlignment="Center"
  GridViewColumnHeader.Click="GridViewColumnHeaderClickedHandler"
 >
```

Příklad definuje obslužnou rutinu události tak, aby směr řazení mění mezi vzestupném a sestupném pořadí pokaždé, když stisknete tlačítko záhlaví sloupce. Následující příklad ukazuje obslužné rutiny události.

```csharp
public partial class Window1 : Window
{
    public Window1()
    {
        InitializeComponent();
    }

    GridViewColumnHeader _lastHeaderClicked = null;
    ListSortDirection _lastDirection = ListSortDirection.Ascending;

    void GridViewColumnHeaderClickedHandler(object sender,
                                            RoutedEventArgs e)
    {
        var headerClicked = e.OriginalSource as GridViewColumnHeader;
        ListSortDirection direction;

        if (headerClicked != null)
        {
            if (headerClicked.Role != GridViewColumnHeaderRole.Padding)
            {
                if (headerClicked != _lastHeaderClicked)
                {
                    direction = ListSortDirection.Ascending;
                }
                else
                {
                    if (_lastDirection == ListSortDirection.Ascending)
                    {
                        direction = ListSortDirection.Descending;
                    }
                    else
                    {
                        direction = ListSortDirection.Ascending;
                    }
                }

                var columnBinding = headerClicked.Column.DisplayMemberBinding as Binding;
                var sortBy = columnBinding?.Path.Path ?? headerClicked.Column.Header as string;

                Sort(sortBy, direction);

                if (direction == ListSortDirection.Ascending)
                {
                    headerClicked.Column.HeaderTemplate =
                      Resources["HeaderTemplateArrowUp"] as DataTemplate;
                }
                else
                {
                    headerClicked.Column.HeaderTemplate =
                      Resources["HeaderTemplateArrowDown"] as DataTemplate;
                }

                // Remove arrow from previously sorted header
                if (_lastHeaderClicked != null && _lastHeaderClicked != headerClicked)
                {
                    _lastHeaderClicked.Column.HeaderTemplate = null;
                }

                _lastHeaderClicked = headerClicked;
                _lastDirection = direction;
            }
        }
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Public Sub New()
        InitializeComponent()
    End Sub

    Private _lastHeaderClicked As GridViewColumnHeader = Nothing
    Private _lastDirection As ListSortDirection = ListSortDirection.Ascending

    Private Sub GridViewColumnHeaderClickedHandler(ByVal sender As Object, ByVal e As RoutedEventArgs)
        Dim headerClicked = TryCast(e.OriginalSource, GridViewColumnHeader)
        Dim direction As ListSortDirection

        If headerClicked IsNot Nothing Then
            If headerClicked.Role <> GridViewColumnHeaderRole.Padding Then
                If headerClicked IsNot _lastHeaderClicked Then
                    direction = ListSortDirection.Ascending
                Else
                    If _lastDirection = ListSortDirection.Ascending Then
                        direction = ListSortDirection.Descending
                    Else
                        direction = ListSortDirection.Ascending
                    End If
                End If

                Dim columnBinding = TryCast(headerClicked.Column.DisplayMemberBinding, Binding)
                Dim sortBy = If(columnBinding?.Path.Path, TryCast(headerClicked.Column.Header, String))

                Sort(sortBy, direction)

                If direction = ListSortDirection.Ascending Then
                    headerClicked.Column.HeaderTemplate = TryCast(Resources("HeaderTemplateArrowUp"), DataTemplate)
                Else
                    headerClicked.Column.HeaderTemplate = TryCast(Resources("HeaderTemplateArrowDown"), DataTemplate)
                End If

                ' Remove arrow from previously sorted header
                If _lastHeaderClicked IsNot Nothing AndAlso _lastHeaderClicked IsNot headerClicked Then
                    _lastHeaderClicked.Column.HeaderTemplate = Nothing
                End If

                _lastHeaderClicked = headerClicked
                _lastDirection = direction
            End If
        End If
    End Sub
End Class
```

Následující příklad ukazuje algoritmus řazení, která je volána k řazení dat. obslužnou rutinou události. Řazení se provádí tak, že vytvoříte nový <xref:System.ComponentModel.SortDescription> struktury.

```csharp
private void Sort(string sortBy, ListSortDirection direction)
{
    ICollectionView dataView =
      CollectionViewSource.GetDefaultView(lv.ItemsSource);

    dataView.SortDescriptions.Clear();
    SortDescription sd = new SortDescription(sortBy, direction);
    dataView.SortDescriptions.Add(sd);
    dataView.Refresh();
}
```

```vb
Private Sub Sort(ByVal sortBy As String, ByVal direction As ListSortDirection)
    Dim dataView As ICollectionView = CollectionViewSource.GetDefaultView(lv.ItemsSource)

    dataView.SortDescriptions.Clear()
    Dim sd As New SortDescription(sortBy, direction)
    dataView.SortDescriptions.Add(sd)
    dataView.Refresh()
End Sub
```

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [ListView – přehled](listview-overview.md)
- [GridView – přehled](gridview-overview.md)
- [Témata s postupy](listview-how-to-topics.md)
