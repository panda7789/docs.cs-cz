---
title: 'Postupy: Generování objektového modelu v jazyce Visual Basic nebo C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 07df915b5c826c7b82f2aaf16fcc22da0361d5f6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781910"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="d20ea-102">Postupy: Generování objektového modelu v Visual Basic nebo C\#</span><span class="sxs-lookup"><span data-stu-id="d20ea-102">How to: Generate the Object Model in Visual Basic or C\#</span></span>
<span data-ttu-id="d20ea-103">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nástroji je objektový model ve vašem vlastním programovacím jazyce mapován na relační databázi.</span><span class="sxs-lookup"><span data-stu-id="d20ea-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="d20ea-104">K dispozici jsou dva nástroje pro automatické generování Visual Basic C# nebo modelu z metadat existující databáze.</span><span class="sxs-lookup"><span data-stu-id="d20ea-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="d20ea-105">Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů k vygenerování objektového modelu.</span><span class="sxs-lookup"><span data-stu-id="d20ea-105">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="d20ea-106">Návrhář o/R poskytuje bohatě uživatelské rozhraní, které vám může pomáhat při [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generování objektového modelu.</span><span class="sxs-lookup"><span data-stu-id="d20ea-106">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="d20ea-107">Další informace najdete v tématu [technologie LINQ to SQL Tools v aplikaci Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="d20ea-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="d20ea-108">Nástroj příkazového řádku SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="d20ea-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="d20ea-109">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d20ea-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d20ea-110">Pokud nemáte existující databázi a chcete ji vytvořit z objektového modelu, můžete vytvořit objektový model pomocí editoru kódu a <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="d20ea-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="d20ea-111">Další informace najdete v tématu [jak: Dynamicky vytvořit databázi](how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="d20ea-111">For more information, see [How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="d20ea-112">Dokumentace k Návrháři O/R poskytuje příklady generování Visual Basic nebo C# objektového modelu pomocí návrháře o/r.</span><span class="sxs-lookup"><span data-stu-id="d20ea-112">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="d20ea-113">Následující informace obsahují příklady použití nástroje příkazového řádku SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="d20ea-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="d20ea-114">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d20ea-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d20ea-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d20ea-115">Example</span></span>  
 <span data-ttu-id="d20ea-116">Příkazový řádek SQLMetal, který je znázorněn v následujícím příkladu, vytvoří kód Visual Basic jako objektový model založený na atributech ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="d20ea-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="d20ea-117">Jsou vykresleny také uložené procedury a funkce.</span><span class="sxs-lookup"><span data-stu-id="d20ea-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="d20ea-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="d20ea-118">Example</span></span>  
 <span data-ttu-id="d20ea-119">Příkazový řádek SQLMetal, který je znázorněn v následujícím příkladu C# , vytvoří kód jako objektový model založený na atributech ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="d20ea-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="d20ea-120">Jsou vykresleny také uložené procedury a funkce a názvy tabulek jsou automaticky v množném čísle.</span><span class="sxs-lookup"><span data-stu-id="d20ea-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="d20ea-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d20ea-121">See also</span></span>

- [<span data-ttu-id="d20ea-122">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="d20ea-122">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="d20ea-123">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d20ea-123">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="d20ea-124">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="d20ea-124">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="d20ea-125">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="d20ea-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="d20ea-126">Mapování na základě atributů</span><span class="sxs-lookup"><span data-stu-id="d20ea-126">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="d20ea-127">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="d20ea-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="d20ea-128">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="d20ea-128">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="d20ea-129">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="d20ea-129">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="d20ea-130">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="d20ea-130">Creating the Object Model</span></span>](creating-the-object-model.md)
