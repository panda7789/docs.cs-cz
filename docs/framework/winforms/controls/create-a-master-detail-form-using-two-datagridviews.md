---
title: 'Postupy: vytvoření hlavního podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c724408ae689f339585267e183061f56b8271a9a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="83968-102">Postupy: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="83968-102">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="83968-103">Následující příklad kódu vytvoří hlavního a podrobného formuláře pomocí dvou <xref:System.Windows.Forms.DataGridView> ovládací prvky vázané na dva <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="83968-103">The following code example creates a master/detail form using two <xref:System.Windows.Forms.DataGridView> controls bound to two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="83968-104">Zdroj dat je <xref:System.Data.DataSet> obsahující `Customers` a `Orders` tabulky z ukázkové databáze Northwind SQL Server spolu s <xref:System.Data.DataRelation> dva prostřednictvím vztahující se `CustomerID` sloupce.</span><span class="sxs-lookup"><span data-stu-id="83968-104">The data source is a <xref:System.Data.DataSet> that contains the `Customers` and `Orders` tables from the Northwind SQL Server sample database along with a <xref:System.Data.DataRelation> that relates the two through the `CustomerID` column.</span></span>  
  
 <span data-ttu-id="83968-105">Jeden <xref:System.Windows.Forms.BindingSource> je vázán k nadřazené `Customers` tabulky v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="83968-105">One <xref:System.Windows.Forms.BindingSource> is bound to the parent `Customers` table in the data set.</span></span> <span data-ttu-id="83968-106">Tato data se zobrazí v hlavní <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="83968-106">This data is displayed in the master <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="83968-107">Druhá <xref:System.Windows.Forms.BindingSource> je vázána na první konektor data.</span><span class="sxs-lookup"><span data-stu-id="83968-107">The other <xref:System.Windows.Forms.BindingSource> is bound to the first data connector.</span></span> <span data-ttu-id="83968-108"><xref:System.Windows.Forms.BindingSource.DataMember%2A> Vlastnost druhý <xref:System.Windows.Forms.BindingSource> je nastaven na <xref:System.Data.DataRelation> název.</span><span class="sxs-lookup"><span data-stu-id="83968-108">The <xref:System.Windows.Forms.BindingSource.DataMember%2A> property of the second <xref:System.Windows.Forms.BindingSource> is set to the <xref:System.Data.DataRelation> name.</span></span> <span data-ttu-id="83968-109">To způsobí, že přidružené podrobností <xref:System.Windows.Forms.DataGridView> zobrazte řádky podřízeného ovládacího prvku `Orders` tabulku, která odpovídají na aktuálním řádku v hlavní <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="83968-109">This causes the associated detail <xref:System.Windows.Forms.DataGridView> control to display the rows of the child `Orders` table that correspond to the current row in the master <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="83968-110">Úplné vysvětlení tento příklad kódu, najdete v části [návod: vytváření hlavního a podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md).</span><span class="sxs-lookup"><span data-stu-id="83968-110">For a complete explanation of this code example, see [Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83968-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="83968-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="83968-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="83968-112">Compiling the Code</span></span>  
 <span data-ttu-id="83968-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="83968-113">This example requires:</span></span>  
  
 <span data-ttu-id="83968-114">Odkazy na systém, System.Data, System.Windows.Forms a System.XML sestavení.</span><span class="sxs-lookup"><span data-stu-id="83968-114">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
-   <span data-ttu-id="83968-115">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="83968-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="83968-116">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="83968-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="83968-117">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="83968-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="83968-118">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="83968-118">.NET Framework Security</span></span>  
 <span data-ttu-id="83968-119">Ukládání citlivé informace, jako jsou hesla, v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="83968-119">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="83968-120">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="83968-120">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="83968-121">Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="83968-121">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83968-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="83968-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="83968-123">Návod: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="83968-123">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 [<span data-ttu-id="83968-124">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="83968-124">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="83968-125">Ochrana informací o připojení</span><span class="sxs-lookup"><span data-stu-id="83968-125">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
