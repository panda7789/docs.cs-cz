---
title: Windows Forms – datová vazba
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: f0267a774d284cac1672ff971d6af3ec3439c84d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540641"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="33675-102">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="33675-102">Windows Forms Data Binding</span></span>
<span data-ttu-id="33675-103">Datové vazby v systému Windows Forms poskytuje způsob, jak zobrazit a provést změny na informace ze zdroje dat v ovládacích prvků formuláře.</span><span class="sxs-lookup"><span data-stu-id="33675-103">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="33675-104">Můžete vázat na zdroje dat tradiční jak téměř jakoukoli struktura, která obsahuje data.</span><span class="sxs-lookup"><span data-stu-id="33675-104">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="33675-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="33675-105">In This Section</span></span>  
 [<span data-ttu-id="33675-106">Datové vazby a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="33675-106">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 <span data-ttu-id="33675-107">Poskytuje přehled datové vazby v systému Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="33675-107">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="33675-108">Zdroje dat podporované rozhraním Windows Forms</span><span class="sxs-lookup"><span data-stu-id="33675-108">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="33675-109">Popisuje zdroje dat, které lze použít s Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="33675-109">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="33675-110">Rozhraní související s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="33675-110">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 <span data-ttu-id="33675-111">Popisuje řadu rozhraní použít s Windows Forms – datová vazba.</span><span class="sxs-lookup"><span data-stu-id="33675-111">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="33675-112">Postupy: Procházení dat v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="33675-112">How to: Navigate Data in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="33675-113">Ukazuje, jak procházet položky ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="33675-113">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="33675-114">Oznámení změn v datové vazbě Windows Forms</span><span class="sxs-lookup"><span data-stu-id="33675-114">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="33675-115">Popisuje různé typy oznámení o změně pro Windows Forms – datová vazba.</span><span class="sxs-lookup"><span data-stu-id="33675-115">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="33675-116">Postupy: Implementace rozhraní INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="33675-116">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="33675-117">Ukazuje, jak implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="33675-117">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="33675-118">Rozhraní komunikuje se připojeného ovládacího prvku změny vlastnost u objektu firmy</span><span class="sxs-lookup"><span data-stu-id="33675-118">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="33675-119">Postupy: Použití vzoru PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="33675-119">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="33675-120">Ukazuje, jak se má použít *PropertyName*vzor změněno na vlastnosti uživatelského ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="33675-120">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="33675-121">Postupy: Implementace rozhraní ITypedList</span><span class="sxs-lookup"><span data-stu-id="33675-121">How to: Implement the ITypedList Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="33675-122">Ukazuje, jak povolit zjišťování aplikace schéma pro vazbu seznamu pomocí implementace <xref:System.ComponentModel.ITypedList> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="33675-122">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="33675-123">Postupy: Implementace rozhraní IListSource</span><span class="sxs-lookup"><span data-stu-id="33675-123">How to: Implement the IListSource Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="33675-124">Ukazuje, jak implementovat <xref:System.ComponentModel.IListSource> neimplementuje rozhraní pro vytvoření třídy vazbu <xref:System.Collections.IList>, ale poskytuje seznam z jiného umístění.</span><span class="sxs-lookup"><span data-stu-id="33675-124">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="33675-125">Postupy: Zajištění, aby více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných</span><span class="sxs-lookup"><span data-stu-id="33675-125">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="33675-126">Ukazuje, jak zpracovat <xref:System.Windows.Forms.BindingSource.BindingComplete> událostí k zajištění všech ovládacích prvků vázaných ke zdroji dat zůstalo synchronizovaných.</span><span class="sxs-lookup"><span data-stu-id="33675-126">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="33675-127">Postupy: Zajištění, aby vybraný řádek v podřízené tabulce zůstal ve správné pozici</span><span class="sxs-lookup"><span data-stu-id="33675-127">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="33675-128">Ukazuje, jak zajistit vybraného řádku podřízené tabulce nezmění, když dojde ke změně na pole v nadřazené tabulce.</span><span class="sxs-lookup"><span data-stu-id="33675-128">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="33675-129">Viz také [rozhraní související s datové vazby](http://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [postup: přejděte dat ve Windows Forms](http://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [postupy: vytvoření jednoduše připojeného ovládacího prvku ve formuláři Windows](http://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="33675-129">Also see [Interfaces Related to Data Binding](http://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [How to: Navigate Data in Windows Forms](http://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [How to: Create a Simple-Bound Control on a Windows Form](http://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="33675-130">Odkaz</span><span class="sxs-lookup"><span data-stu-id="33675-130">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="33675-131">Popisuje třídy, která představuje vazbu mezi vazbu součástí a zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="33675-131">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="33675-132">Popisuje třídy, který zapouzdřuje zdroj dat pro vytvoření vazby na ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="33675-132">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="33675-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="33675-133">Related Sections</span></span>  
 [<span data-ttu-id="33675-134">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="33675-134">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 <span data-ttu-id="33675-135">Obsahuje seznam témat, která ukazují, jak používat <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="33675-135">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="33675-136">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="33675-136">DataGridView Control</span></span>](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="33675-137">Poskytuje seznam témat, která ukazují, jak používat ovládací prvek datagrid vazbu.</span><span class="sxs-lookup"><span data-stu-id="33675-137">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="33675-138">Viz také [přístup k datům v sadě Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="33675-138">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
