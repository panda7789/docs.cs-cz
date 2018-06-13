---
title: Analýza technologie LINQ to SQL zdrojového kódu
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 25c54fa67171b456b2eeb5c30f52d1e654fca995
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353751"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="d6361-102">Analýza technologie LINQ to SQL zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="d6361-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="d6361-103">Pomocí následujících kroků můžete vytvořit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zdrojový kód z ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="d6361-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="d6361-104">Můžete porovnat elementy objektový model elementy databáze lépe zobrazíte jak různé položky, které jsou namapované.</span><span class="sxs-lookup"><span data-stu-id="d6361-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6361-105">Vývojáři pomocí sady Visual Studio můžete použít [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] k vytvoření tohoto kódu.</span><span class="sxs-lookup"><span data-stu-id="d6361-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to produce this code.</span></span>  
  
1.  <span data-ttu-id="d6361-106">Pokud jste již nemají ukázková databáze Northwind ve svém vývojovém počítači, můžete stáhnout zdarma.</span><span class="sxs-lookup"><span data-stu-id="d6361-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="d6361-107">Další informace najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="d6361-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2.  <span data-ttu-id="d6361-108">Pomocí nástroje příkazového řádku na SqlMetal ke generování zdrojový soubor Visual Basic a C#.</span><span class="sxs-lookup"><span data-stu-id="d6361-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="d6361-109">Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d6361-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="d6361-110">Zadáním následujících příkazů v příkazovém řádku může generovat Visual Basic a C# zdrojové soubory, které zahrnují uložené procedury a funkce:</span><span class="sxs-lookup"><span data-stu-id="d6361-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="d6361-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6361-111">See Also</span></span>  
 [<span data-ttu-id="d6361-112">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="d6361-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [<span data-ttu-id="d6361-113">Základní informace</span><span class="sxs-lookup"><span data-stu-id="d6361-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
