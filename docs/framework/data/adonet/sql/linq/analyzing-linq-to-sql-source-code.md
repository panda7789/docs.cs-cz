---
title: Analýza zdrojového kódu LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 4b23e0df1ee762dd22d43cd1be050db70481db50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964112"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="2db7c-102">Analýza zdrojového kódu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2db7c-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="2db7c-103">Pomocí následujících kroků můžete ze vzorové databáze Northwind [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nakládat zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="2db7c-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="2db7c-104">Můžete porovnat prvky objektového modelu s prvky databáze, abyste lépe viděli, jak jsou namapovány různé položky.</span><span class="sxs-lookup"><span data-stu-id="2db7c-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2db7c-105">Vývojáři, kteří používají Visual Studio, mohou k tvorbě tohoto kódu použít návrháře O/R.</span><span class="sxs-lookup"><span data-stu-id="2db7c-105">Developers using Visual Studio can use the O/R Designer to produce this code.</span></span>  
  
1. <span data-ttu-id="2db7c-106">Pokud ještě nemáte ukázkovou databázi Northwind ve vývojovém počítači, můžete si ji stáhnout zdarma.</span><span class="sxs-lookup"><span data-stu-id="2db7c-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="2db7c-107">Další informace najdete v tématu [stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="2db7c-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2. <span data-ttu-id="2db7c-108">K vygenerování Visual Basic nebo C# zdrojového souboru použijte nástroj příkazového řádku SqlMetal.</span><span class="sxs-lookup"><span data-stu-id="2db7c-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="2db7c-109">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="2db7c-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="2db7c-110">Zadáním následujících příkazů na příkazovém řádku můžete vygenerovat Visual Basic a C# zdrojové soubory, které zahrnují uložené procedury a funkce:</span><span class="sxs-lookup"><span data-stu-id="2db7c-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="2db7c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2db7c-111">See also</span></span>

- [<span data-ttu-id="2db7c-112">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="2db7c-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="2db7c-113">Základní informace</span><span class="sxs-lookup"><span data-stu-id="2db7c-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
