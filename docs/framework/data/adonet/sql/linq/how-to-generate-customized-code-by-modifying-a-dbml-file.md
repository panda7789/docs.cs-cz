---
title: 'Postupy: generování přizpůsobených kódu úpravou souboru DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 806d0ebc0e9ce970e144d80dbbd4910f9d271e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354569"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Postupy: generování přizpůsobených kódu úpravou souboru DBML
Zdrojový kód jazyka Visual Basic nebo C# můžete vygenerovat ze souboru metadat databáze markup language (dbml). Tento přístup poskytuje možnost přizpůsobit výchozí soubor DBML před generováním mapování kódu aplikace. Toto je pokročilá funkce.  
  
 Takto vypadají kroky v tomto procesu:  
  
1.  Generování souboru DBML.  
  
2.  K úpravě souboru DBML použijte editor. Všimněte si, že soubor DBML musíte ověřit proti souboru schématu definice (XSD) pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] soubory dbml. Další informace najdete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
3.  Generování zdrojového kódu Visual Basic a C#.  
  
 Následující příklady pomocí nástroje příkazového řádku na SQLMetal. Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří soubor DBML z ukázková databáze Northwind. Jako zdroj pro metadata databáze můžete použít název databáze nebo název souboru MDF.  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Příklad  
 Následující kód generuje souboru zdrojového kódu Visual Basic a C# ze souboru DBML.  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Viz také  
 [Generování kódu v LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
