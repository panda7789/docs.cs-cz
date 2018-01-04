---
title: "Analýza technologie LINQ to SQL zdrojového kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 730ecffc9543c8a1184bc41ab77d9aec9b53b5a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="analyzing-linq-to-sql-source-code"></a>Analýza technologie LINQ to SQL zdrojového kódu
Pomocí následujících kroků můžete vytvořit [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zdrojový kód z ukázková databáze Northwind. Můžete porovnat elementy objektový model elementy databáze lépe zobrazíte jak různé položky, které jsou namapované.  
  
> [!NOTE]
>  Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] k vytvoření tohoto kódu.  
  
1.  Pokud jste již nemají ukázková databáze Northwind ve svém vývojovém počítači, můžete stáhnout zdarma. Další informace najdete v tématu [stažení ukázkové databáze](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
2.  Pomocí nástroje příkazového řádku na SqlMetal ke generování zdrojový soubor Visual Basic a C#. Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Zadáním následujících příkazů v příkazovém řádku může generovat Visual Basic a C# zdrojové soubory, které zahrnují uložené procedury a funkce:  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Viz také  
 [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
