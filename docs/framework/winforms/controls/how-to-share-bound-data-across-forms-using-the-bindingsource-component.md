---
title: 'Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: 28eceaec72053d70885d54bc09179cff743ff71c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591433"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="8b972-102">Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource</span><span class="sxs-lookup"><span data-stu-id="8b972-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="8b972-103">Data můžete jednoduše sdílet mezi formuláři pomocí <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="8b972-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="8b972-104">Chcete třeba zobrazit jeden formulář jen pro čtení, která shrnuje data zdroje dat a jiné Upravitelný formulář, který obsahuje podrobné informace o aktuálně vybrané položky ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="8b972-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="8b972-105">Tento příklad ukazuje tento scénář.</span><span class="sxs-lookup"><span data-stu-id="8b972-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b972-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b972-106">Example</span></span>  
 <span data-ttu-id="8b972-107">Následující příklad kódu ukazuje, jak sdílet <xref:System.Windows.Forms.BindingSource> a vázaných dat mezi formuláři.</span><span class="sxs-lookup"><span data-stu-id="8b972-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="8b972-108">V tomto příkladu, sdílený <xref:System.Windows.Forms.BindingSource> je předán konstruktoru podřízeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="8b972-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="8b972-109">Podřízený formulář umožňuje uživateli upravit data pro aktuálně vybrané položky v hlavním formuláři.</span><span class="sxs-lookup"><span data-stu-id="8b972-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b972-110"><xref:System.Windows.Forms.BindingSource.BindingComplete> Událost pro <xref:System.Windows.Forms.BindingSource> komponenta je zpracována v příklad k zajištění toho, že dvě různými formami zůstaly synchronizované.</span><span class="sxs-lookup"><span data-stu-id="8b972-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="8b972-111">Další informace o tom, proč se to, najdete v článku [jak: Zajištění více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných](../multiple-controls-bound-to-data-source-synchronized.md).</span><span class="sxs-lookup"><span data-stu-id="8b972-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8b972-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8b972-112">Compiling the Code</span></span>  
 <span data-ttu-id="8b972-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="8b972-113">This example requires:</span></span>  
  
- <span data-ttu-id="8b972-114">Odkazy na sestavení systému, System.Windows.Forms, System.Drawing, System.Data a System.Xml.</span><span class="sxs-lookup"><span data-stu-id="8b972-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b972-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b972-115">See also</span></span>

- [<span data-ttu-id="8b972-116">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="8b972-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="8b972-117">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="8b972-117">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="8b972-118">Postupy: Zpracování chyb a výjimek, ke kterým dochází s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="8b972-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
