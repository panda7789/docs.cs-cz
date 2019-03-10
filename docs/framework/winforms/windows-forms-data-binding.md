---
title: Windows Forms – datová vazba
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: ed456807137e8cf7594bc50eb0eebb67b88e6b40
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704603"
---
# <a name="windows-forms-data-binding"></a>Windows Forms – datová vazba
Datové vazby v modelu Windows Forms poskytuje způsob, jak zobrazit a udělat změny informací ze zdroje dat v ovládacích prvcích ve formuláři. Můžete svázat do zdroje dat pro tradiční i téměř jakoukoli strukturu, která obsahuje data.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Datové vazby a Windows Forms](data-binding-and-windows-forms.md)  
 Poskytuje přehled datové vazby v modelu Windows Forms.  
  
 [Zdroje dat podporované rozhraním Windows Forms](data-sources-supported-by-windows-forms.md)  
 Popisuje zdroje dat, které lze použít s Windows Forms.  
  
 [Rozhraní související s datovou vazbou](interfaces-related-to-data-binding.md)  
 Popisuje několik součástí Windows Forms – datová vazba rozhraní.  
  
 [Postupy: Procházení dat v modelu Windows Forms](how-to-navigate-data-in-windows-forms.md)  
 Ukazuje, jak přejděte přes položky ve zdroji dat.  
  
 [Oznámení změn v datové vazbě Windows Forms](change-notification-in-windows-forms-data-binding.md)  
 Popisuje různé typy oznámení o změně pro Windows Forms – datová vazba.  
  
 [Postupy: Implementace rozhraní INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md)  
 Ukazuje, jak implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Rozhraní komunikuje s vázaného ovládacího prvku změny vlastností na obchodní objekt  
  
 [Postupy: Použití vzoru PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)  
 Ukazuje, jak použít *PropertyName*vzor změněné na vlastnosti uživatelského ovládacího prvku Windows Forms.  
  
 [Postupy: Implementace rozhraní ITypedList](how-to-implement-the-itypedlist-interface.md)  
 Ukazuje, jak povolit zjišťování schématu s možností vazby seznam implementací <xref:System.ComponentModel.ITypedList> rozhraní.  
  
 [Postupy: Implementace rozhraní IListSource](how-to-implement-the-ilistsource-interface.md)  
 Ukazuje, jak implementovat <xref:System.ComponentModel.IListSource> neimplementuje rozhraní pro vytvoření třídy s možností vazby <xref:System.Collections.IList>, ale poskytuje seznam z jiného umístění.  
  
 [Postupy: Zajištění více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných](multiple-controls-bound-to-data-source-synchronized.md)  
 Ukazuje, jak zpracovat <xref:System.Windows.Forms.BindingSource.BindingComplete> událostí, aby všechny ovládací prvky vázané na zdroji dat zůstalo synchronizovaných.  
  
 [Postupy: Zajistěte, aby že vybraný řádek v podřízené tabulce zůstal ve správné pozici](ensure-the-selected-row-in-a-child-table-correct.md)  
 Ukazuje, jak zajistit vybraný řádek v podřízené tabulce nemění, když ke změně pole nadřazené tabulky.  
  
 Viz také [související rozhraní datové vazby](interfaces-related-to-data-binding.md), [jak: Procházení dat v modelu Windows Forms](how-to-navigate-data-in-windows-forms.md), a [jak: Vytvoření jednoduše vázaného ovládacího prvku ve formuláři Windows Forms](how-to-create-a-simple-bound-control-on-a-windows-form.md).  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 Popisuje třídy, která představuje vazbu mezi umožňujících vazbu součástí a zdroji dat.  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 Popisuje třídy, který zapouzdřuje zdroj dat pro vytvoření vazby na ovládací prvky.  
  
## <a name="related-sections"></a>Související oddíly  
 [Komponenta BindingSource](./controls/bindingsource-component.md)  
 Obsahuje seznam témat, které ukazují, jak používat <xref:System.Windows.Forms.BindingSource> komponenty.  
  
 [Ovládací prvek DataGridView](./controls/datagridview-control-windows-forms.md)  
 Obsahuje seznam témat, která ukazují, jak použít ovládací prvek datagrid s možností vazby.  
  
 Viz také [přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).
