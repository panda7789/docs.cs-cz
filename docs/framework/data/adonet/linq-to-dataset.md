---
title: LINQ na DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 4995512336ee9eb6e33df011757ed533db57e76e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783785"
---
# <a name="linq-to-dataset"></a>LINQ na DataSet
LINQ to DataSet usnadňuje a urychlují dotazování na data uložená v <xref:System.Data.DataSet> objektu. Konkrétně LINQ to DataSet zjednodušuje dotazování tím, že vývojářům umožňuje psát dotazy z samotného programovacího jazyka namísto použití samostatného dotazovacího jazyka. To je užitečné hlavně pro vývojáře v aplikaci Visual Studio, kteří nyní mohou využít kontrolu syntaxe při kompilaci, statického typování a podporu technologie IntelliSense, kterou poskytuje Visual Studio ve svých dotazech.  
  
 LINQ to DataSet lze také použít k dotazování na data, která byla konsolidována z jednoho nebo více zdrojů dat. Díky tomu je možné mnoha scénářů, které vyžadují flexibilitu při reprezentaci a zpracování dat, jako je dotazování na místně agregovaná data a ukládání do střední vrstvy ve webových aplikacích. Tato metoda manipulace vyžaduje zejména obecné vytváření sestav, analýzy a business intelligence aplikace.  
  
 Funkce LINQ to DataSet je vystavena hlavně prostřednictvím rozšiřujících metod v <xref:System.Data.DataRowExtensions> třídách a. <xref:System.Data.DataTableExtensions> LINQ to DataSet vytváří a používá stávající architekturu ADO.NET a není určena k nahrazení ADO.NET v kódu aplikace. Existující kód ADO.NET bude nadále fungovat v aplikaci LINQ to DataSet. V následujícím diagramu je znázorněn vztah LINQ to DataSet k ADO.NET a úložiště dat.  
  
 ![Diagram znázorňující, že LINQ to DataSet je založen na poskytovateli ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](getting-started-linq-to-dataset.md)  
  
 [Průvodce programováním](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Reference  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Viz také:

- [LINQ (Language-Integrated Query) –C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (Language-Integrated Query) – Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ a ADO.NET](linq-and-ado-net.md)
- [ADO.NET](index.md)
