---
title: 'Postupy: generování přizpůsobeného kódu úpravou souboru DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 6619f4b8c0a47b36a0b84fa21bab4109d26ef895
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002953"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="10876-102">Postupy: generování přizpůsobeného kódu úpravou souboru DBML</span><span class="sxs-lookup"><span data-stu-id="10876-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="10876-103">Můžete vygenerovat Visual Basic nebo C# zdrojový kód ze souboru metadat jazyka pro označení databáze (. dbml).</span><span class="sxs-lookup"><span data-stu-id="10876-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="10876-104">Tento přístup poskytuje příležitost k přizpůsobení výchozího souboru. dbml před tím, než vygenerujete kód mapování aplikace.</span><span class="sxs-lookup"><span data-stu-id="10876-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="10876-105">Toto je pokročilá funkce.</span><span class="sxs-lookup"><span data-stu-id="10876-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="10876-106">Postup v tomto procesu je následující:</span><span class="sxs-lookup"><span data-stu-id="10876-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="10876-107">Vygenerujte soubor. dbml.</span><span class="sxs-lookup"><span data-stu-id="10876-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="10876-108">Použijte editor pro úpravu souboru. dbml.</span><span class="sxs-lookup"><span data-stu-id="10876-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="10876-109">Všimněte si, že soubor. dbml se musí ověřit proti souboru definice schématu (. XSD) pro soubory [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. dbml.</span><span class="sxs-lookup"><span data-stu-id="10876-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="10876-110">Další informace naleznete v tématu [generování kódu v LINQ to SQL](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="10876-110">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="10876-111">Vygenerujte Visual Basic nebo C# zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="10876-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="10876-112">V následujících příkladech se používá nástroj příkazového řádku SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="10876-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="10876-113">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="10876-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10876-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="10876-114">Example</span></span>  
 <span data-ttu-id="10876-115">Následující kód vygeneruje soubor. dbml z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="10876-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="10876-116">Jako zdroj pro metadata databáze můžete použít buď název databáze, nebo název souboru. mdf.</span><span class="sxs-lookup"><span data-stu-id="10876-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="10876-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="10876-117">Example</span></span>  
 <span data-ttu-id="10876-118">Následující kód generuje Visual Basic nebo C# soubor zdrojového kódu ze souboru. dbml.</span><span class="sxs-lookup"><span data-stu-id="10876-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="10876-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10876-119">See also</span></span>

- [<span data-ttu-id="10876-120">Generování kódu v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="10876-120">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="10876-121">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="10876-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="10876-122">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="10876-122">Creating the Object Model</span></span>](creating-the-object-model.md)
