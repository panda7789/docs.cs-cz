---
title: "Postupy: generování přizpůsobených kódu úpravou souboru DBML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 743e938df0b9c7f12a9c3a11a4b5558137add529
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="b319c-102">Postupy: generování přizpůsobených kódu úpravou souboru DBML</span><span class="sxs-lookup"><span data-stu-id="b319c-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="b319c-103">Můžete vygenerovat [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] nebo zdrojového kódu C# ze souboru metadat databáze markup language (dbml).</span><span class="sxs-lookup"><span data-stu-id="b319c-103">You can generate [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="b319c-104">Tento přístup poskytuje možnost přizpůsobit výchozí soubor DBML před generováním mapování kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="b319c-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="b319c-105">Toto je pokročilá funkce.</span><span class="sxs-lookup"><span data-stu-id="b319c-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="b319c-106">Takto vypadají kroky v tomto procesu:</span><span class="sxs-lookup"><span data-stu-id="b319c-106">The steps in this process are as follows:</span></span>  
  
1.  <span data-ttu-id="b319c-107">Generování souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="b319c-107">Generate a .dbml file.</span></span>  
  
2.  <span data-ttu-id="b319c-108">K úpravě souboru DBML použijte editor.</span><span class="sxs-lookup"><span data-stu-id="b319c-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="b319c-109">Všimněte si, že soubor DBML musíte ověřit proti souboru schématu definice (XSD) pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] soubory dbml.</span><span class="sxs-lookup"><span data-stu-id="b319c-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="b319c-110">Další informace najdete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b319c-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3.  <span data-ttu-id="b319c-111">Vygenerovat [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] nebo zdrojového kódu C#.</span><span class="sxs-lookup"><span data-stu-id="b319c-111">Generate the [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# source code.</span></span>  
  
 <span data-ttu-id="b319c-112">Následující příklady pomocí nástroje příkazového řádku na SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="b319c-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="b319c-113">Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b319c-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b319c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="b319c-114">Example</span></span>  
 <span data-ttu-id="b319c-115">Následující kód vytvoří soubor DBML z ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="b319c-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="b319c-116">Jako zdroj pro metadata databáze můžete použít název databáze nebo název souboru MDF.</span><span class="sxs-lookup"><span data-stu-id="b319c-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="b319c-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="b319c-117">Example</span></span>  
 <span data-ttu-id="b319c-118">Následující kód vytvoří [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] nebo C# souboru zdrojového kódu ze souboru DBML.</span><span class="sxs-lookup"><span data-stu-id="b319c-118">The following code generates [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="b319c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b319c-119">See Also</span></span>  
 [<span data-ttu-id="b319c-120">Generování kódu v technologii LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b319c-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="b319c-121">SqlMetal.exe (nástroj pro vytváření kódu)</span><span class="sxs-lookup"><span data-stu-id="b319c-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="b319c-122">Vytváření objektový Model</span><span class="sxs-lookup"><span data-stu-id="b319c-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
