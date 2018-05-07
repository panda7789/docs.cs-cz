---
title: Analýza technologie LINQ to SQL zdrojového kódu
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 25c54fa67171b456b2eeb5c30f52d1e654fca995
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="analyzing-linq-to-sql-source-code"></a>Analýza technologie LINQ to SQL zdrojového kódu
Pomocí následujících kroků můžete vytvořit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zdrojový kód z ukázková databáze Northwind. Můžete porovnat elementy objektový model elementy databáze lépe zobrazíte jak různé položky, které jsou namapované.  
  
> [!NOTE]
>  Vývojáři pomocí sady Visual Studio můžete použít [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] k vytvoření tohoto kódu.  
  
1.  Pokud jste již nemají ukázková databáze Northwind ve svém vývojovém počítači, můžete stáhnout zdarma. Další informace najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
2.  Pomocí nástroje příkazového řádku na SqlMetal ke generování zdrojový soubor Visual Basic a C#. Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Zadáním následujících příkazů v příkazovém řádku může generovat Visual Basic a C# zdrojové soubory, které zahrnují uložené procedury a funkce:  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Viz také  
 [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
