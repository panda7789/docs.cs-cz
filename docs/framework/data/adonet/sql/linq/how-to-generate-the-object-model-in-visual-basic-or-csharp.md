---
title: 'Postupy: Generování objektového modelu v jazyce Visual Basic nebo C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 07df915b5c826c7b82f2aaf16fcc22da0361d5f6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781910"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Postupy: Generování objektového modelu v Visual Basic nebo C\#
V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nástroji je objektový model ve vašem vlastním programovacím jazyce mapován na relační databázi. K dispozici jsou dva nástroje pro automatické generování Visual Basic C# nebo modelu z metadat existující databáze.  
  
- Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů k vygenerování objektového modelu. Návrhář o/R poskytuje bohatě uživatelské rozhraní, které vám může pomáhat při [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generování objektového modelu. Další informace najdete v tématu [technologie LINQ to SQL Tools v aplikaci Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
- Nástroj příkazového řádku SQLMetal. Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    > Pokud nemáte existující databázi a chcete ji vytvořit z objektového modelu, můžete vytvořit objektový model pomocí editoru kódu a <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Další informace najdete v tématu [jak: Dynamicky vytvořit databázi](how-to-dynamically-create-a-database.md).  
  
 Dokumentace k Návrháři O/R poskytuje příklady generování Visual Basic nebo C# objektového modelu pomocí návrháře o/r. Následující informace obsahují příklady použití nástroje příkazového řádku SQLMetal. Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Příklad  
 Příkazový řádek SQLMetal, který je znázorněn v následujícím příkladu, vytvoří kód Visual Basic jako objektový model založený na atributech ukázkové databáze Northwind. Jsou vykresleny také uložené procedury a funkce.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Příklad  
 Příkazový řádek SQLMetal, který je znázorněn v následujícím příkladu C# , vytvoří kód jako objektový model založený na atributech ukázkové databáze Northwind. Jsou vykresleny také uložené procedury a funkce a názvy tabulek jsou automaticky v množném čísle.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním](programming-guide.md)
- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
- [Učení podle návodů](learning-by-walkthroughs.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Mapování na základě atributů](attribute-based-mapping.md)
- [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Externí mapování](external-mapping.md)
- [Stažení ukázkových databází](downloading-sample-databases.md)
- [Vytvoření objektového modelu](creating-the-object-model.md)
