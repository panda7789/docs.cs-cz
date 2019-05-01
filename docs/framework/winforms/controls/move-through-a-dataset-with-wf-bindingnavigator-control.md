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
ms.openlocfilehash: d76c2e5882c9df94674294da00ba446dfbfd2b3a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012734"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="f0a3c-102">Postupy: Pohyb v prvku DataSet pomocí ovládacího prvku Windows Forms BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="f0a3c-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="f0a3c-103">Při sestavování aplikací řízených daty, často musíte pro zobrazení kolekce dat pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="f0a3c-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="f0a3c-104"><xref:System.Windows.Forms.BindingNavigator> Ovládacího prvku, v kombinaci s <xref:System.Windows.Forms.BindingSource> komponenty, poskytuje pohodlný a rozšiřitelné řešení pro přesun v kolekci a zobrazení postupně na položky.</span><span class="sxs-lookup"><span data-stu-id="f0a3c-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0a3c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0a3c-105">Example</span></span>  
 <span data-ttu-id="f0a3c-106">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.BindingNavigator> ovládací prvek procházejte data.</span><span class="sxs-lookup"><span data-stu-id="f0a3c-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="f0a3c-107">Je součástí sady <xref:System.Data.DataView>, který je vázán na <xref:System.Windows.Forms.TextBox> ovládacím prvkem <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="f0a3c-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0a3c-108">Ukládání citlivých informací, jako jsou hesla, v rámci připojovací řetězec může ovlivnit zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="f0a3c-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="f0a3c-109">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="f0a3c-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="f0a3c-110">Další informace najdete v tématu [chrání informace o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="f0a3c-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f0a3c-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f0a3c-111">Compiling the Code</span></span>  
 <span data-ttu-id="f0a3c-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f0a3c-112">This example requires:</span></span>  
  
- <span data-ttu-id="f0a3c-113">Odkazy na sestavení systému, System.Data, System.Drawing, System.Windows.Forms a System.Xml.</span><span class="sxs-lookup"><span data-stu-id="f0a3c-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="f0a3c-114">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f0a3c-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f0a3c-115">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="f0a3c-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0a3c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0a3c-116">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="f0a3c-117">Ovládací prvek BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="f0a3c-117">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="f0a3c-118">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="f0a3c-118">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="f0a3c-119">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="f0a3c-119">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
