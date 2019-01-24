---
title: 'Postupy: Generování přizpůsobeného kódu úpravou souboru DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: b17743f20cf9fcb01cdd39dc7afc3f6b4419ebff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499090"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Postupy: Generování přizpůsobeného kódu úpravou souboru DBML
Můžete generovat jazyka Visual Basic nebo C# zdrojového kódu ze souboru metadat databáze markup language (dbml). Tento přístup vám dává příležitost k přizpůsobení výchozího souboru .dbml před generováním mapování kódu aplikace. Jde o pokročilou funkci.  
  
 Kroky v tomto procesu jsou následující:  
  
1.  Vygenerování souboru .dbml.  
  
2.  Použijte editor k úpravě souboru .dbml. Všimněte si, že souboru .dbml musí ověřovat proti souboru (XSD) definice schématu pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] soubory dbml. Další informace najdete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
3.  Generovat jazyka Visual Basic nebo C# zdrojový kód.  
  
 Následující příklady používají nástroj příkazového řádku SQLMetal. Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Příklad  
 Následující kód vygeneruje souboru .dbml z ukázkové databáze Northwind. Jako zdroj pro metadata databáze můžete použít název databáze nebo název souboru MDF.  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Příklad  
 Následující kód vygeneruje jazyka Visual Basic nebo C# souboru zdrojového kódu ze souboru .dbml.  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Viz také:
- [Generování kódu v LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
