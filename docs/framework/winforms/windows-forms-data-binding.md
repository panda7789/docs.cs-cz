---
title: Datová vazba
description: Naučte se používat datové vazby v model Windows Forms k zobrazení a provádění změn informací ze zdroje dat v ovládacích prvcích ve formuláři.
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 3dfce24147caf9b138916ca8dc3b7a9010439f58
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325546"
---
# <a name="windows-forms-data-binding"></a>Windows Forms – datová vazba
Datová vazba v model Windows Forms poskytuje prostředky pro zobrazení a provádění změn informací ze zdroje dat v ovládacích prvcích ve formuláři. Můžete vytvořit propojení s tradičními zdroji dat i s téměř jakoukoli strukturou, která obsahuje data.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Datové vazby a rozhraní Windows Forms](data-binding-and-windows-forms.md)  
 Poskytuje přehled datové vazby v model Windows Forms.  
  
 [Zdroje dat podporované rozhraním Windows Forms](data-sources-supported-by-windows-forms.md)  
 Popisuje zdroje dat, které lze použít s model Windows Forms.  
  
 [Rozhraní související s datovou vazbou](interfaces-related-to-data-binding.md)  
 Popisuje několik rozhraní používaných s model Windows Forms datovou vazbou.  
  
 [Postupy: Procházení dat v rozhraní Windows Forms](how-to-navigate-data-in-windows-forms.md)  
 Ukazuje, jak procházet položky ve zdroji dat.  
  
 [Oznámení změn v datové vazbě rozhraní Windows Forms](change-notification-in-windows-forms-data-binding.md)  
 Popisuje různé typy oznámení o změně pro model Windows Forms datovou vazbu.  
  
 [Postupy: Implementace rozhraní INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md)  
 Ukazuje, jak implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Rozhraní komunikuje s vázaným ovládacím prvkem o změny vlastností u podnikového objektu.  
  
 [Postupy: Použití vzoru PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)  
 Ukazuje, jak použít vzor typu *PropertyName*změněné na vlastnosti model Windows Forms uživatelského ovládacího prvku.  
  
 [Postupy: Implementace rozhraní ITypedList](how-to-implement-the-itypedlist-interface.md)  
 Ukazuje, jak povolit zjišťování schématu pro seznam s možností vazby implementací <xref:System.ComponentModel.ITypedList> rozhraní.  
  
 [Postupy: Implementace rozhraní IListSource](how-to-implement-the-ilistsource-interface.md)  
 Ukazuje, jak implementovat <xref:System.ComponentModel.IListSource> rozhraní pro vytvoření třídy s možností vazby neimplementuje <xref:System.Collections.IList> , ale poskytuje seznam z jiného umístění.  
  
 [Postupy: Zajištění, aby více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných](multiple-controls-bound-to-data-source-synchronized.md)  
 Ukazuje, jak zpracovat <xref:System.Windows.Forms.BindingSource.BindingComplete> událost, aby se zajistilo, že všechny ovládací prvky svázané se zdrojem dat zůstanou synchronizované.  
  
 [Postupy: Zajištění, aby vybraný řádek v podřízené tabulce zůstal ve správné pozici](ensure-the-selected-row-in-a-child-table-correct.md)  
 Ukazuje, jak zajistit, aby se vybraný řádek v podřízené tabulce nezmění, když je provedena změna v poli nadřazené tabulky.  
  
 Viz také [rozhraní související s datovou vazbou](interfaces-related-to-data-binding.md), [Postupy: navigace mezi daty v model Windows Forms](how-to-navigate-data-in-windows-forms.md)a [Postup: vytvoření jednoduchého ovládacího prvku na formuláři Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md).  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 Popisuje třídu, která představuje vazbu mezi komponentou s možností vazby a zdrojem dat.  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 Popisuje třídu, která zapouzdřuje zdroj dat pro vazbu k ovládacím prvkům.  
  
## <a name="related-sections"></a>Související oddíly  
 [Komponenta BindingSource](./controls/bindingsource-component.md)  
 Obsahuje seznam témat, která ukazují, jak používat <xref:System.Windows.Forms.BindingSource> součást.  
  
 [DataGridView – ovládací prvek](./controls/datagridview-control-windows-forms.md)  
 Poskytuje seznam témat, která ukazují, jak použít vázaný ovládací prvek DataGrid.  
  
 Viz také [přístup k datům v aplikaci Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).
