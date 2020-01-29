---
title: Vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], creating
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
ms.openlocfilehash: d317f4e592790c9b48b539b1601814569e14529f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737330"
---
# <a name="how-to-create-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a><span data-ttu-id="2d909-102">Postupy: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="2d909-102">How to: Create a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="2d909-103">Následující příklad kódu vytvoří hlavní a podrobný formulář pomocí dvou <xref:System.Windows.Forms.DataGridView>ch ovládacích prvků vázaných na dvě komponenty <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="2d909-103">The following code example creates a master/detail form using two <xref:System.Windows.Forms.DataGridView> controls bound to two <xref:System.Windows.Forms.BindingSource> components.</span></span> <span data-ttu-id="2d909-104">Zdroj dat je <xref:System.Data.DataSet>, který obsahuje tabulky `Customers` a `Orders` ze vzorové databáze Northwind SQL Server společně s <xref:System.Data.DataRelation>, který vztahují dva sloupce `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="2d909-104">The data source is a <xref:System.Data.DataSet> that contains the `Customers` and `Orders` tables from the Northwind SQL Server sample database along with a <xref:System.Data.DataRelation> that relates the two through the `CustomerID` column.</span></span>  
  
 <span data-ttu-id="2d909-105">Jedna <xref:System.Windows.Forms.BindingSource> je svázána s nadřazenou `Customers` tabulkou v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="2d909-105">One <xref:System.Windows.Forms.BindingSource> is bound to the parent `Customers` table in the data set.</span></span> <span data-ttu-id="2d909-106">Tato data se zobrazí v ovládacím prvku hlavní <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="2d909-106">This data is displayed in the master <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="2d909-107">Druhý <xref:System.Windows.Forms.BindingSource> je svázán s prvním datovým konektorem.</span><span class="sxs-lookup"><span data-stu-id="2d909-107">The other <xref:System.Windows.Forms.BindingSource> is bound to the first data connector.</span></span> <span data-ttu-id="2d909-108">Vlastnost <xref:System.Windows.Forms.BindingSource.DataMember%2A> druhého <xref:System.Windows.Forms.BindingSource> je nastavena na hodnotu <xref:System.Data.DataRelation> název.</span><span class="sxs-lookup"><span data-stu-id="2d909-108">The <xref:System.Windows.Forms.BindingSource.DataMember%2A> property of the second <xref:System.Windows.Forms.BindingSource> is set to the <xref:System.Data.DataRelation> name.</span></span> <span data-ttu-id="2d909-109">To způsobí, že přidružený ovládací prvek <xref:System.Windows.Forms.DataGridView> ovládacího prvku zobrazit řádky podřízené tabulky `Orders`, která odpovídá aktuálnímu řádku v ovládacím prvku hlavní <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="2d909-109">This causes the associated detail <xref:System.Windows.Forms.DataGridView> control to display the rows of the child `Orders` table that correspond to the current row in the master <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="2d909-110">Úplný popis tohoto příkladu kódu naleznete v tématu [Návod: Vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků model Windows Forms DataGridView](creating-a-master-detail-form-using-two-datagridviews.md).</span><span class="sxs-lookup"><span data-stu-id="2d909-110">For a complete explanation of this code example, see [Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls](creating-a-master-detail-form-using-two-datagridviews.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d909-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d909-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2d909-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2d909-112">Compiling the Code</span></span>  
 <span data-ttu-id="2d909-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2d909-113">This example requires:</span></span>  
  
 <span data-ttu-id="2d909-114">Odkazy na sestavení System, System. data, System. Windows. Forms a System. XML.</span><span class="sxs-lookup"><span data-stu-id="2d909-114">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2d909-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2d909-115">.NET Framework Security</span></span>  
 <span data-ttu-id="2d909-116">Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d909-116">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="2d909-117">Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="2d909-117">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="2d909-118">Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="2d909-118">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d909-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d909-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="2d909-120">Návod: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="2d909-120">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)
- [<span data-ttu-id="2d909-121">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="2d909-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2d909-122">Ochrana informací o připojení</span><span class="sxs-lookup"><span data-stu-id="2d909-122">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
