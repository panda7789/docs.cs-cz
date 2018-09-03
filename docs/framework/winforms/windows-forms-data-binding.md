---
title: Windows Forms – datová vazba
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: cfb4c59c76142420f479b0b16a6d80317e98d159
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486007"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="d0d88-102">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="d0d88-102">Windows Forms Data Binding</span></span>
<span data-ttu-id="d0d88-103">Datové vazby v modelu Windows Forms poskytuje způsob, jak zobrazit a udělat změny informací ze zdroje dat v ovládacích prvcích ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="d0d88-103">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="d0d88-104">Můžete svázat do zdroje dat pro tradiční i téměř jakoukoli strukturu, která obsahuje data.</span><span class="sxs-lookup"><span data-stu-id="d0d88-104">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0d88-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d0d88-105">In This Section</span></span>  
 [<span data-ttu-id="d0d88-106">Datové vazby a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0d88-106">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 <span data-ttu-id="d0d88-107">Poskytuje přehled datové vazby v modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d0d88-107">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="d0d88-108">Zdroje dat podporované rozhraním Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0d88-108">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="d0d88-109">Popisuje zdroje dat, které lze použít s Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d0d88-109">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="d0d88-110">Rozhraní související s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="d0d88-110">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 <span data-ttu-id="d0d88-111">Popisuje několik součástí Windows Forms – datová vazba rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d0d88-111">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="d0d88-112">Postupy: Procházení dat v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0d88-112">How to: Navigate Data in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="d0d88-113">Ukazuje, jak přejděte přes položky ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="d0d88-113">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="d0d88-114">Oznámení změn v datové vazbě Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0d88-114">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="d0d88-115">Popisuje různé typy oznámení o změně pro Windows Forms – datová vazba.</span><span class="sxs-lookup"><span data-stu-id="d0d88-115">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="d0d88-116">Postupy: Implementace rozhraní INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="d0d88-116">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="d0d88-117">Ukazuje, jak implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d0d88-117">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="d0d88-118">Rozhraní komunikuje s vázaného ovládacího prvku změny vlastností na obchodní objekt</span><span class="sxs-lookup"><span data-stu-id="d0d88-118">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="d0d88-119">Postupy: Použití vzoru PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="d0d88-119">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="d0d88-120">Ukazuje, jak použít *PropertyName*vzor změněné na vlastnosti uživatelského ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d0d88-120">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="d0d88-121">Postupy: Implementace rozhraní ITypedList</span><span class="sxs-lookup"><span data-stu-id="d0d88-121">How to: Implement the ITypedList Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="d0d88-122">Ukazuje, jak povolit zjišťování schématu s možností vazby seznam implementací <xref:System.ComponentModel.ITypedList> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d0d88-122">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="d0d88-123">Postupy: Implementace rozhraní IListSource</span><span class="sxs-lookup"><span data-stu-id="d0d88-123">How to: Implement the IListSource Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="d0d88-124">Ukazuje, jak implementovat <xref:System.ComponentModel.IListSource> neimplementuje rozhraní pro vytvoření třídy s možností vazby <xref:System.Collections.IList>, ale poskytuje seznam z jiného umístění.</span><span class="sxs-lookup"><span data-stu-id="d0d88-124">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="d0d88-125">Postupy: Zajištění, aby více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných</span><span class="sxs-lookup"><span data-stu-id="d0d88-125">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="d0d88-126">Ukazuje, jak zpracovat <xref:System.Windows.Forms.BindingSource.BindingComplete> událostí, aby všechny ovládací prvky vázané na zdroji dat zůstalo synchronizovaných.</span><span class="sxs-lookup"><span data-stu-id="d0d88-126">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="d0d88-127">Postupy: Zajištění, aby vybraný řádek v podřízené tabulce zůstal ve správné pozici</span><span class="sxs-lookup"><span data-stu-id="d0d88-127">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="d0d88-128">Ukazuje, jak zajistit vybraný řádek v podřízené tabulce nemění, když ke změně pole nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="d0d88-128">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="d0d88-129">Také naleznete v tématu [související rozhraní datové vazby](https://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [postupy: procházení dat v modelu Windows Forms](https://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [postupy: vytvoření jednoduše vázaného ovládacího prvku ve formuláři Windows Forms](https://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="d0d88-129">Also see [Interfaces Related to Data Binding](https://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [How to: Navigate Data in Windows Forms](https://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [How to: Create a Simple-Bound Control on a Windows Form](https://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d0d88-130">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d0d88-130">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="d0d88-131">Popisuje třídy, která představuje vazbu mezi umožňujících vazbu součástí a zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="d0d88-131">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="d0d88-132">Popisuje třídy, který zapouzdřuje zdroj dat pro vytvoření vazby na ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d0d88-132">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d0d88-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d0d88-133">Related Sections</span></span>  
 [<span data-ttu-id="d0d88-134">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="d0d88-134">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 <span data-ttu-id="d0d88-135">Obsahuje seznam témat, které ukazují, jak používat <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="d0d88-135">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="d0d88-136">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="d0d88-136">DataGridView Control</span></span>](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="d0d88-137">Obsahuje seznam témat, která ukazují, jak použít ovládací prvek datagrid s možností vazby.</span><span class="sxs-lookup"><span data-stu-id="d0d88-137">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="d0d88-138">Viz také [přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="d0d88-138">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
