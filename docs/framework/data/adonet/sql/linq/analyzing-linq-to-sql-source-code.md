---
title: Analýza zdrojového kódu LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 1110e64d16a6c2790939cc695ecd67e37ec109e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203285"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="32891-102">Analýza zdrojového kódu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="32891-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="32891-103">Pomocí následujících kroků můžete vytvářet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zdrojový kód z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="32891-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="32891-104">Můžete porovnat jsou mapovány prvky modelu objektu s prvky databáze pro lepší naleznete v tématu jak různé položky.</span><span class="sxs-lookup"><span data-stu-id="32891-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32891-105">Pomocí sady Visual Studio mohou vývojáři [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] vytvoří tento kód.</span><span class="sxs-lookup"><span data-stu-id="32891-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to produce this code.</span></span>  
  
1.  <span data-ttu-id="32891-106">Pokud nemáte již Northwind ukázkovou databázi na vašem vývojovém počítači, můžete stáhnout zdarma.</span><span class="sxs-lookup"><span data-stu-id="32891-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="32891-107">Další informace najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="32891-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2.  <span data-ttu-id="32891-108">Pomocí nástroje příkazového řádku SqlMetal k vygenerování jazyka Visual Basic nebo C# zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="32891-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="32891-109">Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="32891-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="32891-110">Zadáním následujících příkazů na příkazovém řádku můžete vygenerovat jazyka Visual Basic a C# zdrojové soubory, které zahrnují uložené procedury a funkce:</span><span class="sxs-lookup"><span data-stu-id="32891-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="32891-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32891-111">See also</span></span>

- [<span data-ttu-id="32891-112">Odkaz</span><span class="sxs-lookup"><span data-stu-id="32891-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="32891-113">Základní informace</span><span class="sxs-lookup"><span data-stu-id="32891-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
