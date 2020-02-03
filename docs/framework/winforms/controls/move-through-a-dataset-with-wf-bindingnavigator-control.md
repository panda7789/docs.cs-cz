---
title: Pohyb přes datovou sadu pomocí ovládacího prvku BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: 73a102da74a3a2a00b5042331cffcaf3d858ea5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742150"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="c7139-102">Postupy: Pohyb v prvku DataSet pomocí ovládacího prvku Windows Forms BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="c7139-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="c7139-103">Při sestavování aplikací založených na datech budete často potřebovat zobrazit kolekce dat pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="c7139-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="c7139-104">Ovládací prvek <xref:System.Windows.Forms.BindingNavigator> společně s komponentou <xref:System.Windows.Forms.BindingSource> poskytuje praktické a rozšiřitelné řešení pro přesun v kolekci a zobrazení položek postupně.</span><span class="sxs-lookup"><span data-stu-id="c7139-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7139-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7139-105">Example</span></span>  
 <span data-ttu-id="c7139-106">Následující příklad kódu ukazuje, jak použít ovládací prvek <xref:System.Windows.Forms.BindingNavigator> k přesunu dat.</span><span class="sxs-lookup"><span data-stu-id="c7139-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="c7139-107">Sada je obsažena v <xref:System.Data.DataView>, která je svázána s ovládacím prvkem <xref:System.Windows.Forms.TextBox> s <xref:System.Windows.Forms.BindingSource> komponentou.</span><span class="sxs-lookup"><span data-stu-id="c7139-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7139-108">Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7139-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="c7139-109">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="c7139-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="c7139-110">Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="c7139-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7139-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c7139-111">Compiling the Code</span></span>  
 <span data-ttu-id="c7139-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c7139-112">This example requires:</span></span>  
  
- <span data-ttu-id="c7139-113">Odkazy na sestavení System, System. data, System. Drawing, System. Windows. Forms a System. XML.</span><span class="sxs-lookup"><span data-stu-id="c7139-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7139-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7139-114">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="c7139-115">Ovládací prvek BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="c7139-115">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="c7139-116">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="c7139-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="c7139-117">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="c7139-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
