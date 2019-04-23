---
title: Analýza zdrojového kódu LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 2d8c5a89cbf09ef3829669a3d5272f742fa6582c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317074"
---
# <a name="analyzing-linq-to-sql-source-code"></a>Analýza zdrojového kódu LINQ to SQL
Pomocí následujících kroků můžete vytvářet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zdrojový kód z ukázkové databáze Northwind. Můžete porovnat jsou mapovány prvky modelu objektu s prvky databáze pro lepší naleznete v tématu jak různé položky.  
  
> [!NOTE]
>  Pomocí sady Visual Studio mohou vývojáři [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] vytvoří tento kód.  
  
1. Pokud nemáte již Northwind ukázkovou databázi na vašem vývojovém počítači, můžete stáhnout zdarma. Další informace najdete v tématu [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
2. Pomocí nástroje příkazového řádku SqlMetal k vygenerování jazyka Visual Basic nebo C# zdrojový soubor. Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Zadáním následujících příkazů na příkazovém řádku můžete vygenerovat jazyka Visual Basic a C# zdrojové soubory, které zahrnují uložené procedury a funkce:  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Viz také:

- [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
