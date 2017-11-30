---
title: "Úvod do LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6fd14840cfffb1a59949251b26c168aada336de9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-linq-c"></a>Úvod do LINQ (C#)
Language-Integrated Query (LINQ) je že novinka zavedená v rozhraní .NET Framework verze 3.5 obsahující mezery mezi world objektů a dat na světě.  
  
 Dotazy na data jsou tradičně, vyjádřené jako jednoduchý řetězce bez kontrolu typu v kompilaci čas nebo podporu technologie IntelliSense. Kromě toho budete muset další různých dotazovací jazyk pro každý typ zdroje dat: SQL databáze, dokumentů XML, různé webové služby a tak dále. Díky LINQ *dotazu* prvotřídní jazyk konstrukce v jazyce C#. Můžete psát dotazy proti silného typu kolekce objektů pomocí známých operátory a klíčová slova jazyka.  
  
 Můžete zápis dotazů LINQ v C# pro databáze systému SQL Server, dokumentů XML, datové sady ADO.NET a kolekci objektů, který podporuje <xref:System.Collections.IEnumerable> nebo obecná <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Podpora LINQ jsou tu taky třetích stran pro mnoho webové služby a jiné implementace databáze.  
  
 Můžete dotazů LINQ v nové projekty nebo spolu s bez LINQ dotazů v existující projekty. Jediným požadavkem je, že projekt cílí na rozhraní .NET Framework 3.5 nebo novější.  
  
 Na následujícím obrázku ze sady Visual Studio ukazuje dotaz LINQ částečně dokončilo proti databázi systému SQL Server v jak C# a Visual Basic s Kontrola úplné typu a podporu technologie IntelliSense.  
  
 ![Dotaz LINQ pomocí Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")  
  
## <a name="next-steps"></a>Další kroky  
 Další podrobnosti o LINQ, spusťte Seznamte se s některé základní pojmy v části Začínáme [Začínáme s dotazy LINQ v jazyku C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), a přečtěte si dokumentaci pro LINQ technologii, která vás zajímá:  
  
-   Databáze systému SQL Server: [technologie LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
  
-   Dokumenty XML: [technologie LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   Datové sady ADO.NET: [LINQ na DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
-   Kolekcí .NET, soubory, a tak dále řetězce: [LINQ na objekty (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Viz také  
 [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
