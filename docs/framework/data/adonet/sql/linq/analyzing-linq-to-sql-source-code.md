---
title: Analýza zdrojového kódu LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: dda19800a9aea0d644740c5378f6d5065181993e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248085"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="4af08-102">Analýza zdrojového kódu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4af08-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="4af08-103">Pomocí následujících kroků můžete ze vzorové databáze Northwind [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nakládat zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="4af08-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="4af08-104">Můžete porovnat prvky objektového modelu s prvky databáze, abyste lépe viděli, jak jsou namapovány různé položky.</span><span class="sxs-lookup"><span data-stu-id="4af08-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4af08-105">Vývojáři, kteří používají Visual Studio, mohou k tvorbě tohoto kódu použít návrháře O/R.</span><span class="sxs-lookup"><span data-stu-id="4af08-105">Developers using Visual Studio can use the O/R Designer to produce this code.</span></span>  
  
1. <span data-ttu-id="4af08-106">Pokud ještě nemáte ukázkovou databázi Northwind ve vývojovém počítači, můžete si ji stáhnout zdarma.</span><span class="sxs-lookup"><span data-stu-id="4af08-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="4af08-107">Další informace najdete v tématu [stažení ukázkových databází](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="4af08-107">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
2. <span data-ttu-id="4af08-108">K vygenerování Visual Basic nebo C# zdrojového souboru použijte nástroj příkazového řádku SqlMetal.</span><span class="sxs-lookup"><span data-stu-id="4af08-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="4af08-109">Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="4af08-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="4af08-110">Zadáním následujících příkazů na příkazovém řádku můžete vygenerovat Visual Basic a C# zdrojové soubory, které zahrnují uložené procedury a funkce:</span><span class="sxs-lookup"><span data-stu-id="4af08-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="4af08-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4af08-111">See also</span></span>

- [<span data-ttu-id="4af08-112">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="4af08-112">Reference</span></span>](reference.md)
- [<span data-ttu-id="4af08-113">Základní informace</span><span class="sxs-lookup"><span data-stu-id="4af08-113">Background Information</span></span>](background-information.md)
