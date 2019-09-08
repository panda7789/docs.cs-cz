---
title: 'Postupy: Generování přizpůsobeného kódu úpravou souboru DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 01890e6b899db6b70049e2d6b8193e5b0f4095fb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781980"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Postupy: Generování přizpůsobeného kódu úpravou souboru DBML
Můžete vygenerovat Visual Basic nebo C# zdrojový kód ze souboru metadat jazyka pro označení databáze (. dbml). Tento přístup poskytuje příležitost k přizpůsobení výchozího souboru. dbml před tím, než vygenerujete kód mapování aplikace. Toto je pokročilá funkce.  
  
 Postup v tomto procesu je následující:  
  
1. Vygenerujte soubor. dbml.  
  
2. Použijte editor pro úpravu souboru. dbml. Všimněte si, že soubor. dbml se musí ověřit proti souboru definice schématu (. XSD) [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pro soubory. dbml. Další informace naleznete v tématu [generování kódu v LINQ to SQL](code-generation-in-linq-to-sql.md).  
  
3. Vygenerujte Visual Basic nebo C# zdrojový kód.  
  
 V následujících příkladech se používá nástroj příkazového řádku SQLMetal. Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Příklad  
 Následující kód vygeneruje soubor. dbml z ukázkové databáze Northwind. Jako zdroj pro metadata databáze můžete použít buď název databáze, nebo název souboru. mdf.  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Příklad  
 Následující kód generuje Visual Basic nebo C# soubor zdrojového kódu ze souboru. dbml.  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Viz také:

- [Generování kódu v LINQ to SQL](code-generation-in-linq-to-sql.md)
- [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Vytvoření objektového modelu](creating-the-object-model.md)
