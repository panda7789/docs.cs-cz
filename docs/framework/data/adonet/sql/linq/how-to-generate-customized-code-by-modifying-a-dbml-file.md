---
title: 'Postupy: Generování přizpůsobeného kódu úpravou souboru DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: f64d323abf124f3bd8aeb684563a08289fa47f7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084066"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="cdc9a-102">Postupy: Generování přizpůsobeného kódu úpravou souboru DBML</span><span class="sxs-lookup"><span data-stu-id="cdc9a-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="cdc9a-103">Můžete generovat jazyka Visual Basic nebo C# zdrojového kódu ze souboru metadat databáze markup language (dbml).</span><span class="sxs-lookup"><span data-stu-id="cdc9a-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="cdc9a-104">Tento přístup vám dává příležitost k přizpůsobení výchozího souboru .dbml před generováním mapování kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="cdc9a-105">Jde o pokročilou funkci.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="cdc9a-106">Kroky v tomto procesu jsou následující:</span><span class="sxs-lookup"><span data-stu-id="cdc9a-106">The steps in this process are as follows:</span></span>  
  
1.  <span data-ttu-id="cdc9a-107">Vygenerování souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-107">Generate a .dbml file.</span></span>  
  
2.  <span data-ttu-id="cdc9a-108">Použijte editor k úpravě souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="cdc9a-109">Všimněte si, že souboru .dbml musí ověřovat proti souboru (XSD) definice schématu pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] soubory dbml.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="cdc9a-110">Další informace najdete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cdc9a-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3.  <span data-ttu-id="cdc9a-111">Generovat jazyka Visual Basic nebo C# zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="cdc9a-112">Následující příklady používají nástroj příkazového řádku SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="cdc9a-113">Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="cdc9a-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdc9a-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="cdc9a-114">Example</span></span>  
 <span data-ttu-id="cdc9a-115">Následující kód vygeneruje souboru .dbml z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="cdc9a-116">Jako zdroj pro metadata databáze můžete použít název databáze nebo název souboru MDF.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="cdc9a-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="cdc9a-117">Example</span></span>  
 <span data-ttu-id="cdc9a-118">Následující kód vygeneruje jazyka Visual Basic nebo C# souboru zdrojového kódu ze souboru .dbml.</span><span class="sxs-lookup"><span data-stu-id="cdc9a-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdc9a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdc9a-119">See also</span></span>

- [<span data-ttu-id="cdc9a-120">Generování kódu v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cdc9a-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="cdc9a-121">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="cdc9a-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="cdc9a-122">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="cdc9a-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
