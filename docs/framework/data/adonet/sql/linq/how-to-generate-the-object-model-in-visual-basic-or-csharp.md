---
title: "Postupy: generování objektový Model v jazyce Visual Basic nebo C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ec28b175dddb98eb035061363dd6581e796280b3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Postupy: generování objektový Model v jazyce Visual Basic nebo C# #
V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], objektový model v vlastní programovací jazyk je namapována na relační databázi. Dva nástroje jsou k dispozici pro automatické generování [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] nebo C# model z metadat existující databázi.  
  
-   Pokud používáte [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ke generování objektový model. [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Nabízí bohaté uživatelské prostředí můžete vygenerovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model. Další informace najdete v tématu [technologie Linq to SQL nástroje v sadě Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
-   Nástroj příkazového řádku SQLMetal. Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    >  Pokud nemáte existující databázi a chcete ho vytvořit objektovém modelu, můžete vytvořit objektový model pomocí kódu editoru a <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Další informace najdete v tématu [postupy: vytvoření dynamicky databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
 Dokumentace pro [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] obsahuje příklady jak vygenerovat [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] nebo objekt modelu C# s použitím [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. Následující informace poskytují příklady, jak používat nástroj příkazového řádku na SQLMetal. Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Příklad  
 Příkazový řádek SQLMetal vidět v následujícím příkladu vytvoří [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] kód jako model na základě atributů objektu ukázková databáze Northwind. Uložené procedury a funkce jsou také vykreslen.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Příklad  
 Příkazový řádek SQLMetal vidět v následujícím příkladu vytvoří jako model na základě atributů objektu ukázková databáze Northwind kód C#. Uložené procedury a funkce jsou také vykresluje a názvy tabulek jsou automaticky pluralized.  
  
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
