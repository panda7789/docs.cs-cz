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
ms.openlocfilehash: aa497194fd4ac65f48773a45175333a1d862b453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956077"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="7b533-102">Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource</span><span class="sxs-lookup"><span data-stu-id="7b533-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="7b533-103">Data můžete v různých formulářích snadno sdílet pomocí <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="7b533-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="7b533-104">Například můžete chtít zobrazit jeden formulář jen pro čtení, který shrnuje data zdrojů dat a další Upravitelný formulář, který obsahuje podrobné informace o aktuálně vybrané položce ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="7b533-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="7b533-105">Tento příklad ukazuje tento scénář.</span><span class="sxs-lookup"><span data-stu-id="7b533-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b533-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b533-106">Example</span></span>  
 <span data-ttu-id="7b533-107">Následující příklad kódu ukazuje, jak sdílet <xref:System.Windows.Forms.BindingSource> a jeho vázaná data napříč formuláři.</span><span class="sxs-lookup"><span data-stu-id="7b533-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="7b533-108">V tomto příkladu je sdílena <xref:System.Windows.Forms.BindingSource> předána konstruktoru podřízeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="7b533-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="7b533-109">Podřízený formulář umožňuje uživateli upravovat data pro aktuálně vybranou položku v hlavním formuláři.</span><span class="sxs-lookup"><span data-stu-id="7b533-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b533-110"><xref:System.Windows.Forms.BindingSource.BindingComplete> Událost<xref:System.Windows.Forms.BindingSource> pro komponentu je zpracována v příkladu, aby bylo zajištěno, že obě formy budou synchronizovány.</span><span class="sxs-lookup"><span data-stu-id="7b533-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="7b533-111">Další informace o tom, proč je to hotové [, najdete v tématu How to: Zajistěte, aby více ovládacích prvků vázaných na](../multiple-controls-bound-to-data-source-synchronized.md)stejný zdroj dat zůstaly synchronizované.</span><span class="sxs-lookup"><span data-stu-id="7b533-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7b533-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7b533-112">Compiling the Code</span></span>  
 <span data-ttu-id="7b533-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7b533-113">This example requires:</span></span>  
  
- <span data-ttu-id="7b533-114">Odkazy na sestavení System, System. Windows. Forms, System. Drawing, System. data a System. XML.</span><span class="sxs-lookup"><span data-stu-id="7b533-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b533-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b533-115">See also</span></span>

- [<span data-ttu-id="7b533-116">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="7b533-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="7b533-117">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="7b533-117">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="7b533-118">Postupy: Zpracování chyb a výjimek, ke kterým dochází s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="7b533-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
