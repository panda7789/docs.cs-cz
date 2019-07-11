---
title: Analýza zdrojového kódu LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: e34364496a791031cc87cf07efd3d2adca39d93c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743588"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="fb12b-102">Analýza zdrojového kódu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="fb12b-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="fb12b-103">Pomocí následujících kroků můžete vytvářet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zdrojový kód z ukázkové databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="fb12b-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="fb12b-104">Můžete porovnat jsou mapovány prvky modelu objektu s prvky databáze pro lepší naleznete v tématu jak různé položky.</span><span class="sxs-lookup"><span data-stu-id="fb12b-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb12b-105">Pomocí sady Visual Studio mohou vývojáři O/R Designer pro vytvoření tohoto kódu.</span><span class="sxs-lookup"><span data-stu-id="fb12b-105">Developers using Visual Studio can use the O/R Designer to produce this code.</span></span>  
  
1. <span data-ttu-id="fb12b-106">Pokud nemáte již Northwind ukázkovou databázi na vašem vývojovém počítači, můžete stáhnout zdarma.</span><span class="sxs-lookup"><span data-stu-id="fb12b-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="fb12b-107">Další informace najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="fb12b-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2. <span data-ttu-id="fb12b-108">Pomocí nástroje příkazového řádku SqlMetal k vygenerování jazyka Visual Basic nebo C# zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="fb12b-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="fb12b-109">Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="fb12b-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="fb12b-110">Zadáním následujících příkazů na příkazovém řádku můžete vygenerovat jazyka Visual Basic a C# zdrojové soubory, které zahrnují uložené procedury a funkce:</span><span class="sxs-lookup"><span data-stu-id="fb12b-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="fb12b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb12b-111">See also</span></span>

- [<span data-ttu-id="fb12b-112">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="fb12b-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="fb12b-113">Základní informace</span><span class="sxs-lookup"><span data-stu-id="fb12b-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
