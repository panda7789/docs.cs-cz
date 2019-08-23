---
title: 'Postupy: Pohyb v prvku DataSet pomocí ovládacího prvku Windows Forms BindingNavigator'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: d33cad4d0a60aa29d8c9f5e2217532963e8358c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952698"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="76f89-102">Postupy: Pohyb v prvku DataSet pomocí ovládacího prvku Windows Forms BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="76f89-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="76f89-103">Při sestavování aplikací založených na datech budete často potřebovat zobrazit kolekce dat pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="76f89-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="76f89-104">Ovládací prvek, ve spojení <xref:System.Windows.Forms.BindingSource> s komponentou, poskytuje pohodlné a rozšiřitelné řešení pro přesun v kolekci a zobrazení položek postupně. <xref:System.Windows.Forms.BindingNavigator></span><span class="sxs-lookup"><span data-stu-id="76f89-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76f89-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="76f89-105">Example</span></span>  
 <span data-ttu-id="76f89-106">Následující příklad kódu ukazuje, jak použít <xref:System.Windows.Forms.BindingNavigator> ovládací prvek k přesunu dat.</span><span class="sxs-lookup"><span data-stu-id="76f89-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="76f89-107">Sada je obsažena v <xref:System.Data.DataView>, která je svázána <xref:System.Windows.Forms.TextBox> s ovládacím prvkem s <xref:System.Windows.Forms.BindingSource> komponentou.</span><span class="sxs-lookup"><span data-stu-id="76f89-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76f89-108">Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="76f89-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="76f89-109">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="76f89-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="76f89-110">Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="76f89-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="76f89-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="76f89-111">Compiling the Code</span></span>  
 <span data-ttu-id="76f89-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="76f89-112">This example requires:</span></span>  
  
- <span data-ttu-id="76f89-113">Odkazy na sestavení System, System. data, System. Drawing, System. Windows. Forms a System. XML.</span><span class="sxs-lookup"><span data-stu-id="76f89-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f89-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76f89-114">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="76f89-115">Ovládací prvek BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="76f89-115">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="76f89-116">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="76f89-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="76f89-117">Postupy: Svázání ovládacího prvku model Windows Forms s typem</span><span class="sxs-lookup"><span data-stu-id="76f89-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
