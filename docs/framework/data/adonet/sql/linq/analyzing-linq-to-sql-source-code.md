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
# <a name="analyzing-linq-to-sql-source-code"></a>Analýza zdrojového kódu LINQ to SQL
Pomocí následujících kroků můžete ze vzorové databáze Northwind [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nakládat zdrojový kód. Můžete porovnat prvky objektového modelu s prvky databáze, abyste lépe viděli, jak jsou namapovány různé položky.  
  
> [!NOTE]
> Vývojáři, kteří používají Visual Studio, mohou k tvorbě tohoto kódu použít návrháře O/R.  
  
1. Pokud ještě nemáte ukázkovou databázi Northwind ve vývojovém počítači, můžete si ji stáhnout zdarma. Další informace najdete v tématu [stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
2. K vygenerování Visual Basic nebo C# zdrojového souboru použijte nástroj příkazového řádku SqlMetal. Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Zadáním následujících příkazů na příkazovém řádku můžete vygenerovat Visual Basic a C# zdrojové soubory, které zahrnují uložené procedury a funkce:  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Viz také:

- [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
