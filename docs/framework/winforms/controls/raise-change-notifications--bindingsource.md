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
ms.openlocfilehash: 7dc640f272226da650a63b1a3434822d21053b48
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968281"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="b5692-102">Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="b5692-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="b5692-103">Komponenta automaticky detekuje změny ve zdroji dat, když typ obsažený ve zdroji dat <xref:System.ComponentModel.INotifyPropertyChanged> implementuje rozhraní a vyvolá <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události při změně hodnoty vlastnosti. <xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="b5692-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="b5692-104">To je užitečné, protože ovládací prvky vázané <xref:System.Windows.Forms.BindingSource> na se budou automaticky aktualizovat podle změny hodnot zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="b5692-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5692-105">Pokud váš zdroj dat implementuje <xref:System.ComponentModel.INotifyPropertyChanged> a provádíte asynchronní operace, neměli byste provádět změny zdroje dat ve vlákně na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b5692-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="b5692-106">Místo toho byste měli číst data ve vlákně na pozadí a slučovat data do seznamu ve vlákně uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b5692-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5692-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5692-107">Example</span></span>  
 <span data-ttu-id="b5692-108">Následující příklad kódu ukazuje jednoduchou implementaci <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b5692-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="b5692-109">Také ukazuje, jak <xref:System.Windows.Forms.BindingSource> automaticky předává zdroj dat do vázaného ovládacího prvku, <xref:System.Windows.Forms.BindingSource> když je svázán se seznamem <xref:System.ComponentModel.INotifyPropertyChanged> typu.</span><span class="sxs-lookup"><span data-stu-id="b5692-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="b5692-110">Použijete `CallerMemberName` -li atribut, volání `NotifyPropertyChanged` metody nemusejí zadávat název vlastnosti jako argument řetězce.</span><span class="sxs-lookup"><span data-stu-id="b5692-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="b5692-111">Další informace naleznete v tématu [informace o volajícím (C#)](../../../csharp/programming-guide/concepts/caller-information.md) nebo [informace o volajícím (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="b5692-111">For more information, see [Caller Information (C#)](../../../csharp/programming-guide/concepts/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b5692-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b5692-112">Compiling the Code</span></span>  
 <span data-ttu-id="b5692-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b5692-113">This example requires:</span></span>  
  
- <span data-ttu-id="b5692-114">Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="b5692-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5692-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5692-115">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="b5692-116">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="b5692-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="b5692-117">Postupy: Vyvolat oznámení o změnách pomocí metody BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="b5692-117">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
