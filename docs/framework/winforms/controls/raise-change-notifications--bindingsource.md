---
title: 'Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 07248ec0b8ac4f2356d9c9915b6a904dfad30cb2
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388971"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="91d3d-102">Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="91d3d-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="91d3d-103">Komponenta <xref:System.Windows.Forms.BindingSource> automaticky rozpozná změny ve zdroji dat, když typ obsažený <xref:System.ComponentModel.INotifyPropertyChanged> ve zdroji <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> dat implementuje rozhraní a vyvolá události při změně hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="91d3d-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="91d3d-104">To je užitečné, protože <xref:System.Windows.Forms.BindingSource> ovládací prvky vázané na bude automaticky aktualizovat jako hodnoty zdroje dat změnit.</span><span class="sxs-lookup"><span data-stu-id="91d3d-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91d3d-105">Pokud váš zdroj <xref:System.ComponentModel.INotifyPropertyChanged> dat implementuje a provádíte asynchronní operace, neměli byste provádět změny zdroje dat ve vlákně na pozadí.</span><span class="sxs-lookup"><span data-stu-id="91d3d-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="91d3d-106">Místo toho byste měli číst data ve vlákně na pozadí a sloučit data do seznamu ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="91d3d-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91d3d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="91d3d-107">Example</span></span>  
 <span data-ttu-id="91d3d-108">Následující příklad kódu ukazuje jednoduchou <xref:System.ComponentModel.INotifyPropertyChanged> implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="91d3d-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="91d3d-109">Také ukazuje, <xref:System.Windows.Forms.BindingSource> jak automaticky předá změnu zdroje <xref:System.Windows.Forms.BindingSource> dat vázanému ovládacímu <xref:System.ComponentModel.INotifyPropertyChanged> prvku, když je vázán na seznam typu.</span><span class="sxs-lookup"><span data-stu-id="91d3d-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="91d3d-110">Pokud použijete `CallerMemberName` atribut, volání `NotifyPropertyChanged` metody není nutné zadat název vlastnosti jako argument řetězce.</span><span class="sxs-lookup"><span data-stu-id="91d3d-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="91d3d-111">Další informace naleznete v [tématu Informace o volajícím (C#)](../../../csharp/language-reference/attributes/caller-information.md) nebo [Informace o volajícím (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="91d3d-111">For more information, see [Caller Information (C#)](../../../csharp/language-reference/attributes/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="91d3d-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="91d3d-112">Compiling the Code</span></span>  
 <span data-ttu-id="91d3d-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="91d3d-113">This example requires:</span></span>  
  
- <span data-ttu-id="91d3d-114">Odkazy na sestavení System, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="91d3d-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d3d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="91d3d-115">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="91d3d-116">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="91d3d-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="91d3d-117">Postupy: Vytváření oznámení o změnách pomocí metody BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="91d3d-117">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
