---
title: 'Postupy: generování objektového modelu v jazyce Visual Basic nebo C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 21266ca2d1230a1afc903734d1b4c53b259e50e1
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50036785"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Postupy: generování objektového modelu v jazyce Visual Basic nebo C# #
V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], objektový model v programovacím jazyce se mapuje na relační databáze. Dva nástroje jsou k dispozici pro automatické generování jazyka Visual Basic nebo C# modelů z metadat existující databázi.  
  
-   Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ke generování objektového modelu. [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Poskytuje bohaté možnosti uživatelského rozhraní můžete generovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model. Další informace najdete v tématu [Linq to SQL nástroje v sadě Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
-   Nástroj příkazového řádku SQLMetal. Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    >  Pokud nemáte stávající databáze a vytvořit jeden z objektového modelu, můžete vytvořit objektový model s použitím kódu editor a <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Další informace najdete v tématu [postupy: Dynamické vytvoření databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
 Dokumentace k [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] obsahuje příklady toho, jak generovat jazyka Visual Basic nebo C# objektový model s použitím [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. Následující informace jsou uvedeny příklady toho, jak pomocí nástroje příkazového řádku SQLMetal. Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Příklad  
 Příkazového řádku SQLMetal je znázorněno v následujícím příkladu kódu jazyka Visual Basic vytvoří jako model založený na atributu objektu z ukázkové databáze Northwind. Uložené procedury a funkce jsou také generovány.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Příklad  
 Je znázorněno v následujícím příkladu příkazového řádku SQLMetal vytváří C# kód jako model založený na atributu objektu z ukázkové databáze Northwind. Uložené procedury a funkce jsou také generovány a názvy tabulek jsou automaticky pluralized.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Učení podle návodů](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [Mapování na základě atributů](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
