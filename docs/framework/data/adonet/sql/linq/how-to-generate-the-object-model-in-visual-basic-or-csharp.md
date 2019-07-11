---
title: 'Postupy: Generování objektového modelu v jazyce Visual Basic nebo C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 24b48b4962ac207f0c6a50456797ff588a97082d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743309"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="fb89b-102">Postupy: Generování objektového modelu v jazyce Visual Basic nebo C\#</span><span class="sxs-lookup"><span data-stu-id="fb89b-102">How to: Generate the Object Model in Visual Basic or C\#</span></span>
<span data-ttu-id="fb89b-103">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], objektový model v programovacím jazyce se mapuje na relační databáze.</span><span class="sxs-lookup"><span data-stu-id="fb89b-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="fb89b-104">Dva nástroje jsou k dispozici pro automatické generování jazyka Visual Basic nebo C# modelů z metadat existující databázi.</span><span class="sxs-lookup"><span data-stu-id="fb89b-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="fb89b-105">Pokud používáte Visual Studio, můžete použít Návrháře relací objektů ke generování objektového modelu.</span><span class="sxs-lookup"><span data-stu-id="fb89b-105">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="fb89b-106">O/R Designer poskytuje bohaté možnosti uživatelského rozhraní můžete generovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="fb89b-106">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="fb89b-107">Další informace najdete v tématu [Linq to SQL nástroje v sadě Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="fb89b-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="fb89b-108">Nástroj příkazového řádku SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="fb89b-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="fb89b-109">Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="fb89b-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fb89b-110">Pokud nemáte stávající databáze a vytvořit jeden z objektového modelu, můžete vytvořit objektový model s použitím kódu editor a <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="fb89b-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="fb89b-111">Další informace najdete v tématu [jak: Dynamické vytvoření databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="fb89b-111">For more information, see [How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="fb89b-112">Dokumentace pro Návrháře relací objektů poskytuje příklady toho, jak generovat jazyka Visual Basic nebo C# objektový model s použitím Návrháře relací objektů.</span><span class="sxs-lookup"><span data-stu-id="fb89b-112">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="fb89b-113">Následující informace jsou uvedeny příklady toho, jak pomocí nástroje příkazového řádku SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="fb89b-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="fb89b-114">Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="fb89b-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb89b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb89b-115">Example</span></span>  
 <span data-ttu-id="fb89b-116">Příkazového řádku SQLMetal je znázorněno v následujícím příkladu kódu jazyka Visual Basic vytvoří jako model založený na atributu objektu z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="fb89b-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="fb89b-117">Uložené procedury a funkce jsou také generovány.</span><span class="sxs-lookup"><span data-stu-id="fb89b-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="fb89b-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb89b-118">Example</span></span>  
 <span data-ttu-id="fb89b-119">Je znázorněno v následujícím příkladu příkazového řádku SQLMetal vytváří C# kód jako model založený na atributu objektu z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="fb89b-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="fb89b-120">Uložené procedury a funkce jsou také generovány a názvy tabulek jsou automaticky pluralized.</span><span class="sxs-lookup"><span data-stu-id="fb89b-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb89b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb89b-121">See also</span></span>

- [<span data-ttu-id="fb89b-122">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="fb89b-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [<span data-ttu-id="fb89b-123">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="fb89b-123">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="fb89b-124">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="fb89b-124">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="fb89b-125">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="fb89b-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="fb89b-126">Mapování na základě atributů</span><span class="sxs-lookup"><span data-stu-id="fb89b-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [<span data-ttu-id="fb89b-127">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="fb89b-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="fb89b-128">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="fb89b-128">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [<span data-ttu-id="fb89b-129">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="fb89b-129">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="fb89b-130">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="fb89b-130">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
