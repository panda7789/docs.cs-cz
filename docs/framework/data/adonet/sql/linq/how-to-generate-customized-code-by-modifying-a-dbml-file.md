---
title: 'Postupy: generování přizpůsobených kódu úpravou souboru DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 806d0ebc0e9ce970e144d80dbbd4910f9d271e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354569"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="0a161-102">Postupy: generování přizpůsobených kódu úpravou souboru DBML</span><span class="sxs-lookup"><span data-stu-id="0a161-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="0a161-103">Zdrojový kód jazyka Visual Basic nebo C# můžete vygenerovat ze souboru metadat databáze markup language (dbml).</span><span class="sxs-lookup"><span data-stu-id="0a161-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="0a161-104">Tento přístup poskytuje možnost přizpůsobit výchozí soubor DBML před generováním mapování kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a161-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="0a161-105">Toto je pokročilá funkce.</span><span class="sxs-lookup"><span data-stu-id="0a161-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="0a161-106">Takto vypadají kroky v tomto procesu:</span><span class="sxs-lookup"><span data-stu-id="0a161-106">The steps in this process are as follows:</span></span>  
  
1.  <span data-ttu-id="0a161-107">Generování souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="0a161-107">Generate a .dbml file.</span></span>  
  
2.  <span data-ttu-id="0a161-108">K úpravě souboru DBML použijte editor.</span><span class="sxs-lookup"><span data-stu-id="0a161-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="0a161-109">Všimněte si, že soubor DBML musíte ověřit proti souboru schématu definice (XSD) pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] soubory dbml.</span><span class="sxs-lookup"><span data-stu-id="0a161-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="0a161-110">Další informace najdete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0a161-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3.  <span data-ttu-id="0a161-111">Generování zdrojového kódu Visual Basic a C#.</span><span class="sxs-lookup"><span data-stu-id="0a161-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="0a161-112">Následující příklady pomocí nástroje příkazového řádku na SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="0a161-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="0a161-113">Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="0a161-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a161-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a161-114">Example</span></span>  
 <span data-ttu-id="0a161-115">Následující kód vytvoří soubor DBML z ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="0a161-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="0a161-116">Jako zdroj pro metadata databáze můžete použít název databáze nebo název souboru MDF.</span><span class="sxs-lookup"><span data-stu-id="0a161-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="0a161-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a161-117">Example</span></span>  
 <span data-ttu-id="0a161-118">Následující kód generuje souboru zdrojového kódu Visual Basic a C# ze souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="0a161-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a161-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a161-119">See Also</span></span>  
 [<span data-ttu-id="0a161-120">Generování kódu v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0a161-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="0a161-121">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="0a161-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="0a161-122">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="0a161-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
