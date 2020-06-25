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
# <a name="windows-forms-data-binding"></a><span data-ttu-id="84d97-103">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="84d97-103">Windows Forms Data Binding</span></span>
<span data-ttu-id="84d97-104">Datová vazba v model Windows Forms poskytuje prostředky pro zobrazení a provádění změn informací ze zdroje dat v ovládacích prvcích ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="84d97-104">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="84d97-105">Můžete vytvořit propojení s tradičními zdroji dat i s téměř jakoukoli strukturou, která obsahuje data.</span><span class="sxs-lookup"><span data-stu-id="84d97-105">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="84d97-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="84d97-106">In This Section</span></span>  
 [<span data-ttu-id="84d97-107">Datové vazby a rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84d97-107">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)  
 <span data-ttu-id="84d97-108">Poskytuje přehled datové vazby v model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="84d97-108">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="84d97-109">Zdroje dat podporované rozhraním Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84d97-109">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="84d97-110">Popisuje zdroje dat, které lze použít s model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="84d97-110">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="84d97-111">Rozhraní související s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="84d97-111">Interfaces Related to Data Binding</span></span>](interfaces-related-to-data-binding.md)  
 <span data-ttu-id="84d97-112">Popisuje několik rozhraní používaných s model Windows Forms datovou vazbou.</span><span class="sxs-lookup"><span data-stu-id="84d97-112">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="84d97-113">Postupy: Procházení dat v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84d97-113">How to: Navigate Data in Windows Forms</span></span>](how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="84d97-114">Ukazuje, jak procházet položky ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="84d97-114">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="84d97-115">Oznámení změn v datové vazbě rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84d97-115">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="84d97-116">Popisuje různé typy oznámení o změně pro model Windows Forms datovou vazbu.</span><span class="sxs-lookup"><span data-stu-id="84d97-116">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="84d97-117">Postupy: Implementace rozhraní INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="84d97-117">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="84d97-118">Ukazuje, jak implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="84d97-118">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="84d97-119">Rozhraní komunikuje s vázaným ovládacím prvkem o změny vlastností u podnikového objektu.</span><span class="sxs-lookup"><span data-stu-id="84d97-119">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="84d97-120">Postupy: Použití vzoru PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="84d97-120">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="84d97-121">Ukazuje, jak použít vzor typu *PropertyName*změněné na vlastnosti model Windows Forms uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="84d97-121">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="84d97-122">Postupy: Implementace rozhraní ITypedList</span><span class="sxs-lookup"><span data-stu-id="84d97-122">How to: Implement the ITypedList Interface</span></span>](how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="84d97-123">Ukazuje, jak povolit zjišťování schématu pro seznam s možností vazby implementací <xref:System.ComponentModel.ITypedList> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="84d97-123">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="84d97-124">Postupy: Implementace rozhraní IListSource</span><span class="sxs-lookup"><span data-stu-id="84d97-124">How to: Implement the IListSource Interface</span></span>](how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="84d97-125">Ukazuje, jak implementovat <xref:System.ComponentModel.IListSource> rozhraní pro vytvoření třídy s možností vazby neimplementuje <xref:System.Collections.IList> , ale poskytuje seznam z jiného umístění.</span><span class="sxs-lookup"><span data-stu-id="84d97-125">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="84d97-126">Postupy: Zajištění, aby více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných</span><span class="sxs-lookup"><span data-stu-id="84d97-126">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="84d97-127">Ukazuje, jak zpracovat <xref:System.Windows.Forms.BindingSource.BindingComplete> událost, aby se zajistilo, že všechny ovládací prvky svázané se zdrojem dat zůstanou synchronizované.</span><span class="sxs-lookup"><span data-stu-id="84d97-127">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="84d97-128">Postupy: Zajištění, aby vybraný řádek v podřízené tabulce zůstal ve správné pozici</span><span class="sxs-lookup"><span data-stu-id="84d97-128">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="84d97-129">Ukazuje, jak zajistit, aby se vybraný řádek v podřízené tabulce nezmění, když je provedena změna v poli nadřazené tabulky.</span><span class="sxs-lookup"><span data-stu-id="84d97-129">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="84d97-130">Viz také [rozhraní související s datovou vazbou](interfaces-related-to-data-binding.md), [Postupy: navigace mezi daty v model Windows Forms](how-to-navigate-data-in-windows-forms.md)a [Postup: vytvoření jednoduchého ovládacího prvku na formuláři Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="84d97-130">Also see [Interfaces Related to Data Binding](interfaces-related-to-data-binding.md), [How to: Navigate Data in Windows Forms](how-to-navigate-data-in-windows-forms.md), and [How to: Create a Simple-Bound Control on a Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="84d97-131">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="84d97-131">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="84d97-132">Popisuje třídu, která představuje vazbu mezi komponentou s možností vazby a zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="84d97-132">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="84d97-133">Popisuje třídu, která zapouzdřuje zdroj dat pro vazbu k ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="84d97-133">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="84d97-134">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="84d97-134">Related Sections</span></span>  
 [<span data-ttu-id="84d97-135">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="84d97-135">BindingSource Component</span></span>](./controls/bindingsource-component.md)  
 <span data-ttu-id="84d97-136">Obsahuje seznam témat, která ukazují, jak používat <xref:System.Windows.Forms.BindingSource> součást.</span><span class="sxs-lookup"><span data-stu-id="84d97-136">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="84d97-137">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="84d97-137">DataGridView Control</span></span>](./controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="84d97-138">Poskytuje seznam témat, která ukazují, jak použít vázaný ovládací prvek DataGrid.</span><span class="sxs-lookup"><span data-stu-id="84d97-138">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="84d97-139">Viz také [přístup k datům v aplikaci Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="84d97-139">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
