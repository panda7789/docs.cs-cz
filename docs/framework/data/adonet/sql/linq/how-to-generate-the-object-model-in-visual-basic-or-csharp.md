---
title: 'Postupy: generování objektového modelu v Visual Basic neboC#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 7d2c0600534c93f5884eec48a4bdaa3ce99945e9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002799"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="e827d-102">Postupy: generování objektového modelu v Visual Basic nebo C\#</span><span class="sxs-lookup"><span data-stu-id="e827d-102">How to: Generate the Object Model in Visual Basic or C\#</span></span>
<span data-ttu-id="e827d-103">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]objektový model vlastního programovacího jazyka je namapován na relační databázi.</span><span class="sxs-lookup"><span data-stu-id="e827d-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="e827d-104">K dispozici jsou dva nástroje pro automatické generování Visual Basic C# nebo modelu z metadat existující databáze.</span><span class="sxs-lookup"><span data-stu-id="e827d-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
- <span data-ttu-id="e827d-105">Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů k vygenerování objektového modelu.</span><span class="sxs-lookup"><span data-stu-id="e827d-105">If you are using Visual Studio, you can use the Object Relational Designer to generate an object model.</span></span> <span data-ttu-id="e827d-106">Návrhář O/R poskytuje bohatě uživatelské rozhraní, které vám umožňuje vygenerovat model [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektů.</span><span class="sxs-lookup"><span data-stu-id="e827d-106">The O/R Designer provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="e827d-107">Další informace najdete v tématu [technologie LINQ to SQL Tools v aplikaci Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="e827d-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
- <span data-ttu-id="e827d-108">Nástroj příkazového řádku SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="e827d-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="e827d-109">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e827d-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e827d-110">Pokud nemáte existující databázi a chcete ji vytvořit z objektového modelu, můžete vytvořit objektový model pomocí editoru kódu a <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span><span class="sxs-lookup"><span data-stu-id="e827d-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="e827d-111">Další informace naleznete v tématu [How to: Dynamic Create a Database](how-to-dynamically-create-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="e827d-111">For more information, see [How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="e827d-112">Dokumentace k Návrháři O/R poskytuje příklady generování Visual Basic nebo C# objektového modelu pomocí návrháře o/r.</span><span class="sxs-lookup"><span data-stu-id="e827d-112">Documentation for the O/R Designer provides examples of how to generate a Visual Basic or C# object model by using the O/R Designer.</span></span> <span data-ttu-id="e827d-113">Následující informace obsahují příklady použití nástroje příkazového řádku SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="e827d-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="e827d-114">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e827d-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e827d-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="e827d-115">Example</span></span>  
 <span data-ttu-id="e827d-116">Příkazový řádek SQLMetal, který je znázorněn v následujícím příkladu, vytvoří kód Visual Basic jako objektový model založený na atributech ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="e827d-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="e827d-117">Jsou vykresleny také uložené procedury a funkce.</span><span class="sxs-lookup"><span data-stu-id="e827d-117">Stored procedures and functions are also rendered.</span></span>  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="e827d-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="e827d-118">Example</span></span>  
 <span data-ttu-id="e827d-119">Příkazový řádek SQLMetal, který je znázorněn v následujícím příkladu C# , vytvoří kód jako objektový model založený na atributech ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="e827d-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="e827d-120">Jsou vykresleny také uložené procedury a funkce a názvy tabulek jsou automaticky v množném čísle.</span><span class="sxs-lookup"><span data-stu-id="e827d-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="e827d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e827d-121">See also</span></span>

- [<span data-ttu-id="e827d-122">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="e827d-122">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="e827d-123">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e827d-123">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="e827d-124">Učení podle návodů</span><span class="sxs-lookup"><span data-stu-id="e827d-124">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="e827d-125">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="e827d-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="e827d-126">Mapování na základě atributů</span><span class="sxs-lookup"><span data-stu-id="e827d-126">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="e827d-127">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="e827d-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="e827d-128">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="e827d-128">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="e827d-129">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="e827d-129">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="e827d-130">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="e827d-130">Creating the Object Model</span></span>](creating-the-object-model.md)
