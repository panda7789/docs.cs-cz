---
title: LINQ to Entities
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 641f9b68-9046-47a1-abb0-1c8eaeda0e2d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c1ef47e6b4f584e0a49482d9eb2ed7bf14602a03
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-entities"></a>LINQ to Entities
Technologie LINQ to Entities podporuje Language-Integrated Query (LINQ), která umožňuje vývojářům psát dotazy pro koncepční model Entity Framework pomocí jazyka Visual Basic a Visual C#. Dotazy na Entity Framework jsou reprezentované pomocí příkazu stromu dotazů, které spustit proti do kontextu objektu. Technologie LINQ to Entities převede Language-Integrated dotazy (LINQ) dotazy pro příkaz stromu dotazy, provádí dotazy na Entity Framework a vrátí objekty, které lze použít k rozhraní Entity Framework a LINQ. Toto je proces pro vytvoření a provedení dotazu LINQ to Entities:  
  
1.  Vytvořit <xref:System.Data.Objects.ObjectQuery%601> instanci z <xref:System.Data.Objects.ObjectContext>.  
  
2.  Napište dotazu LINQ to Entities v C# nebo Visual Basic pomocí <xref:System.Data.Objects.ObjectQuery%601> instance.  
  
3.  LINQ standardní operátory dotazu a výrazy převeďte na strom příkazů.  
  
4.  Spuštění dotazu a v příkazu stromu reprezentace na zdroji dat. Jakékoli výjimky vydané ve zdroji dat během provádění se předávají přímo až klienta.  
  
5.  Vrátí výsledky dotazu zpět do klienta.  
  
## <a name="constructing-an-objectquery-instance"></a>Vytváření instanci ObjectQuery  
 <xref:System.Data.Objects.ObjectQuery%601> Obecná třída reprezentuje dotaz, který vrátí kolekce nula nebo více zadaných entit. Dotaz na objekt se obvykle vytvářejí na základě existující objekt kontextu, místo ručně vytvářen a vždy patří do tohoto objektu kontextu. Tento kontext poskytuje připojení a informace o metadatech, které je potřeba vytvořit a provést dotaz. <xref:System.Data.Objects.ObjectQuery%601> – Obecná třída implementuje <xref:System.Linq.IQueryable%601> obecné rozhraní, jejichž metody Tvůrce povolit dotazů LINQ má být sestaven postupně. Můžete také nechat kompilátoru odvození typu entit s použitím jazyka C# `var` – klíčové slovo (`Dim` v jazyce Visual Basic, s odvození místního typu povoleno).  
  
## <a name="composing-the-queries"></a>Skládání dotazy  
 Instance <xref:System.Data.Objects.ObjectQuery%601> – obecná třída, která implementuje obecná <xref:System.Linq.IQueryable%601> rozhraní, sloužit jako zdroj dat pro LINQ na dotazy entity. V dotazu je zadat přesně informace, které chcete načíst z datového zdroje. Dotaz můžete také určit, jak tyto informace by měl být seřazeny, seskupené a ve tvaru před vrácením. Dotaz je v technologii LINQ, uložené v proměnné. Tato proměnná dotazu neprovede žádnou akci a vrátí žádná data; ukládá jenom informace o dotazu. Po vytvoření dotazu je třeba spustit tento dotaz pro načtení žádná data.  
  
 Technologie LINQ to Entities dotazy můžete sestavit v dva různé syntaxe: výraz syntaxe využívající dotazy a syntaxe dotazu na základě metod. Syntaxe výrazu dotazu a syntaxe dotazu na základě metod jsou nové v C# 3.0 a 9.0 Visual Basic.  
  
 Další informace najdete v tématu [dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md).  
  
## <a name="query-conversion"></a>Převod dotazů  
 K provedení dotazu LINQ to Entities proti rozhraní Entity Framework, musí dotaz LINQ převést na strom znázornění příkaz, může být spuštěn proti rozhraní Entity Framework.  
  
 Technologie LINQ to Entities dotazy se skládají z LINQ standardní operátory dotazu (například <xref:System.Linq.Queryable.Select%2A>, <xref:System.Linq.Queryable.Where%2A>, a <xref:System.Linq.Queryable.GroupBy%2A>) a výrazy (x > 10, Contact.LastName a tak dále). LINQ operátory nejsou definované třídou, ale spíš jsou metody pro třídu. V technologii LINQ, může obsahovat výrazy nic povolenou typů v rámci <xref:System.Linq.Expressions> obor názvů a rozšíření, všechno, co může být reprezentován ve funkci lambda. Toto je nadmnožinou výrazy, které jsou povoleny rozhraní Entity Framework, které jsou podle definice omezen na operace povolené v databázi a nepodporuje <xref:System.Data.Objects.ObjectQuery%601>.  
  
 V rozhraní Entity Framework operátory a výrazy jsou reprezentované pomocí jednoho typu hierarchie, které pak jsou umístěny ve stromu příkazů. Stromu příkazů se používá rozhraní k provedení dotazu. Pokud dotaz LINQ nemůže být vyjádřena jako strom příkazů, bude vyvolána výjimka, pokud dotaz, který je převáděn. Převod LINQ na dotazy na entity zahrnuje dvě dílčí převody: převod standardní operátory dotazu a převod výrazy.  
  
 Existuje několik LINQ standardních operátorů dotazu, které nemají platný posunutí v technologii LINQ to Entities. Pokusy o použití těchto operátorů způsobí výjimku v době překlad dotazů. Seznam podporovaných technologie LINQ to Entities operátory najdete v tématu [podporované a nepodporované metody LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md).  
  
 Další informace o používání standardní operátory dotazu v technologii LINQ to Entities najdete v tématu [standardní operátory dotazu v technologii LINQ to Entities dotazy](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md).  
  
 Obecně platí na serveru, se vyhodnotí výrazy v technologii LINQ to Entities tak chování výraz nesmí lze očekávat, postupujte podle sémantiku CLR. Další informace najdete v tématu [výrazy v technologii LINQ to Entities dotazy](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md).  
  
 Informace o mapování volání metod CLR jsou kanonické funkce ve zdroji dat najdete v tématu [CLR metodu pro mapování kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
 Informace o tom, jak volat kanonický, databáze a vlastní funkce uvnitř [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy, najdete v části [volání funkce v technologii LINQ to Entities dotazy](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md).  
  
## <a name="query-execution"></a>Provádění dotazů  
 Po vytvoření dotaz LINQ uživatelem jsou převedeny na znázornění, který je kompatibilní s rozhraní Entity Framework (ve formě stromy příkazů), které se pak spustí na zdroji dat. Během provádění dotazu se vyhodnocují všechny výrazy dotazů (nebo součásti dotazu) v klientovi nebo na serveru. To zahrnuje výrazy, které se používají ve výsledku materialization nebo entity projekce. Další informace najdete v tématu [provádění dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md). Informace o tom, jak zvýšit výkon, kompilování dotazu jednou a potom ho spustíte několikrát s odlišnými parametry, najdete v článku [zkompilovat dotazy (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).  
  
## <a name="materialization"></a>Vlastnost materialization  
 Vlastnost materialization je proces vrácení výsledků dotazu zpět do klienta jako typy CLR. V technologii LINQ to Entities jsou záznamy dat výsledky dotazu nikdy nevrátilo; je vždy základní typ CLR, definované uživatelem, nebo pomocí rozhraní Entity Framework nebo generované kompilátorem (anonymní typy). Všechny materialization objektu je prováděno pomocí rozhraní Entity Framework. Výjimky vyvolání během objekt materialization způsobí, že všechny chyby, které jsou výsledkem nebylo možné mezi rozhraní Entity Framework a modulu CLR.  
  
 Výsledky dotazu jsou obvykle vrátil jako jeden z následujících akcí:  
  
-   Kolekce nula nebo více objektů zadané entity nebo projekci komplexních typů definovanou v konceptuálním modelu.  
  
-   Typy CLR, které jsou podporovány [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  
  
-   Vložené kolekce.  
  
-   Anonymní typy.  
  
 Další informace najdete v tématu [výsledky dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
  
 [Výrazy v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)  
  
 [Volání funkcí v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
  
 [Kompilované dotazy (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)  
  
 [Provádění dotazů](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)  
  
 [Výsledky dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md)  
  
 [Standardní operátory dotazů LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md)  
  
 [Metoda CLR pro mapování kanonických funkcí](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)  
  
 [Podporované a nepodporované metody LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
  
 [Známé problémy a aspekty u LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)  
  
## <a name="see-also"></a>Viz také  
 [Známé problémy a aspekty u LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ a ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
