---
title: "Postupy: generování objektový Model v jazyce Visual Basic nebo C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6ff5a314fb4264f57f1db3e8475a2e3105897f19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="33304-102">Postupy: generování objektový Model v jazyce Visual Basic nebo C#</span><span class="sxs-lookup"><span data-stu-id="33304-102">How to: Generate the Object Model in Visual Basic or C#</span></span> #
<span data-ttu-id="33304-103">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], objektový model v vlastní programovací jazyk je namapována na relační databázi.</span><span class="sxs-lookup"><span data-stu-id="33304-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="33304-104">Dva nástroje jsou k dispozici pro automatické generování [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] nebo C# model z metadat existující databázi.</span><span class="sxs-lookup"><span data-stu-id="33304-104">Two tools are available for automatically generating a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# model from the metadata of an existing database.</span></span>  
  
-   <span data-ttu-id="33304-105">Pokud používáte [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ke generování objektový model.</span><span class="sxs-lookup"><span data-stu-id="33304-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to generate an object model.</span></span> <span data-ttu-id="33304-106">[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Nabízí bohaté uživatelské prostředí můžete vygenerovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model.</span><span class="sxs-lookup"><span data-stu-id="33304-106">The [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="33304-107">Další informace najdete v tématu [technologie Linq to SQL nástroje v sadě Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="33304-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
-   <span data-ttu-id="33304-108">Nástroj příkazového řádku SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="33304-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="33304-109">Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="33304-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33304-110">Pokud nemáte existující databázi a chcete ho vytvořit objektovém modelu, můžete vytvořit objektový model pomocí kódu editoru a <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="33304-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="33304-111">Další informace najdete v tématu [postupy: vytvoření dynamicky databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="33304-111">For more information, see [How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="33304-112">Dokumentace pro [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] obsahuje příklady jak vygenerovat [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] nebo objekt modelu C# s použitím [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33304-112">Documentation for the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides examples of how to generate a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# object model by using the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span></span> <span data-ttu-id="33304-113">Následující informace poskytují příklady, jak používat nástroj příkazového řádku na SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="33304-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="33304-114">Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="33304-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33304-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="33304-115">Example</span></span>  
 <span data-ttu-id="33304-116">Příkazový řádek SQLMetal vidět v následujícím příkladu vytvoří [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] kód jako model na základě atributů objektu ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="33304-116">The SQLMetal command line shown in the following example produces [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="33304-117">Uložené procedury a funkce jsou také vykreslen.</span><span class="sxs-lookup"><span data-stu-id="33304-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="33304-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="33304-118">Example</span></span>  
 <span data-ttu-id="33304-119">Příkazový řádek SQLMetal vidět v následujícím příkladu vytvoří jako model na základě atributů objektu ukázková databáze Northwind kód C#.</span><span class="sxs-lookup"><span data-stu-id="33304-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="33304-120">Uložené procedury a funkce jsou také vykresluje a názvy tabulek jsou automaticky pluralized.</span><span class="sxs-lookup"><span data-stu-id="33304-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="33304-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="33304-121">See Also</span></span>  
 [<span data-ttu-id="33304-122">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="33304-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [<span data-ttu-id="33304-123">Technologie LINQ to SQL objektový Model</span><span class="sxs-lookup"><span data-stu-id="33304-123">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="33304-124">Učení dle návody</span><span class="sxs-lookup"><span data-stu-id="33304-124">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="33304-125">Postupy: přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="33304-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [<span data-ttu-id="33304-126">Na základě atributů mapování</span><span class="sxs-lookup"><span data-stu-id="33304-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="33304-127">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="33304-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="33304-128">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="33304-128">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [<span data-ttu-id="33304-129">Stažení ukázkové databáze</span><span class="sxs-lookup"><span data-stu-id="33304-129">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="33304-130">Vytváření objektový Model</span><span class="sxs-lookup"><span data-stu-id="33304-130">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
