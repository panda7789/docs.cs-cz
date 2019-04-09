---
title: LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 641f9b68-9046-47a1-abb0-1c8eaeda0e2d
ms.openlocfilehash: 29980450bd75c6ba0992ad7fd3165f6f2d5f32bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129685"
---
# <a name="linq-to-entities"></a>LINQ to Entities
Technologie LINQ to Entities poskytuje podporu Language-Integrated Query (LINQ), který vývojářům umožňuje psát dotazy proti konceptuálního modelu Entity Framework pomocí jazyka Visual Basic nebo Visual C#. Dotazy na Entity Framework jsou reprezentovány dotazy ve stromové struktuře příkaz, které se spustí s do kontextu objektu. Technologie LINQ to Entities převede dotazů LINQ (Language Integrated) dotazy s příkazem strom dotazů, spustí dotazy na Entity Framework a vrátí objekty, které můžete použít Entity Framework a LINQ. Proces pro vytváření a spouštění technologie LINQ to Entities dotazu je následující:  
  
1.  Vytvoření <xref:System.Data.Objects.ObjectQuery%601> instance z <xref:System.Data.Objects.ObjectContext>.  
  
2.  Vytvoření LINQ to Entities dotazů v C# nebo Visual Basic pomocí <xref:System.Data.Objects.ObjectQuery%601> instance.  
  
3.  Převeďte na stromy příkazů operátory standardního dotazu LINQ a výrazy.  
  
4.  Provedení dotazu, v reprezentaci příkazu stromu, zdroji dat. Výjimky vyvolané při provádění na zdroji dat jsou předány přímo do klienta.  
  
5.  Výsledky dotazu vrátíte zpět do klienta.  
  
## <a name="constructing-an-objectquery-instance"></a>Vytváření instanci ObjectQuery  
 <xref:System.Data.Objects.ObjectQuery%601> Generické třídě představuje dotaz, který vrátí kolekci nula nebo více typy entit. K objektu dotazu je obvykle vytvořen z existujícího kontextu objektu, ne právě vytvořený ručně a vždy patří do daného kontextu objektu. Tento kontext poskytuje připojení a informace o metadatech, který je potřeba vytvořit a spustit dotaz. <xref:System.Data.Objects.ObjectQuery%601> Obecná třída implementuje <xref:System.Linq.IQueryable%601> obecné rozhraní, jejíž metody Tvůrce povolení LINQ dotazy, které mají být sestaveny postupně. Můžete také nechat kompilátor odvodit typ entity s použitím jazyka C# `var` – klíčové slovo (`Dim` v jazyce Visual Basic s odvození místního typu povolené).  
  
## <a name="composing-the-queries"></a>Skládání dotazů  
 Instance <xref:System.Data.Objects.ObjectQuery%601> obecnou třídu, která implementuje obecné <xref:System.Linq.IQueryable%601> rozhraní, sloužit jako zdroj dat pro funkci LINQ na dotazy na entity. V dotazu je zadat přesně informace, které chcete načíst ze zdroje dat. Dotaz můžete také určit, jak tyto informace by měl být seřazeny, seskupeny a tvarovány dříve, než se vrátí. V LINQ dotaz uložené v proměnné. Tato proměnná dotazu neprovede žádnou akci a nevrátí žádná data; ukládá pouze informace o dotazu. Po vytvoření dotazu je třeba spustit tento dotaz pro načtení žádná data.  
  
 Může být složené dotazech LINQ to Entities ve dvou různých syntaxí: výraz syntaxe využívající dotazy a syntaxe dotazů založených na volání metody. Syntaxe výrazu dotazu a syntaxe dotazů založených na volání metody jsou nové v C# 3.0 a Visual Basic 9.0.  
  
 Další informace najdete v tématu [dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md).  
  
## <a name="query-conversion"></a>Převod dotazu  
 K provedení LINQ to Entities dotaz na rozhraní Entity Framework, musí být převeden dotazu LINQ k reprezentaci příkazu stromu, který jde provést proti Entity Framework.  
  
 Dotazech LINQ to Entities se skládají z operátory standardního dotazu LINQ (například <xref:System.Linq.Queryable.Select%2A>, <xref:System.Linq.Queryable.Where%2A>, a <xref:System.Linq.Queryable.GroupBy%2A>) a výrazy (x > 10 Contact.LastName a tak dále). Operátory LINQ nejsou definované třídou, ale místo toho jsou metody ve třídě. V technologii LINQ, výrazy mohou obsahovat cokoli, co povoluje typy v rámci <xref:System.Linq.Expressions> obor názvů a při rozšíření i pro cokoli, co může být reprezentována ve funkci lambda. Toto je nadmnožinou výrazů, které jsou povolené rozhraním Entity Framework, které jsou podle definice s omezením pomocí specifikátoru operacím povolené v databázi a podporuje <xref:System.Data.Objects.ObjectQuery%601>.  
  
 V Entity Framework operátory a výrazy jsou reprezentovány hierarchii jeden typ, který pak jsou umístěny ve stromu příkazů. Strom příkazů používá Entity Framework k provedení dotazu. Pokud dotaz LINQ nelze vyjádřen jako strom příkazů, bude vyvolána výjimka, při převodu dotazu. Převod LINQ na dotazy na entity zahrnuje dvě dílčí převody: převod standardních operátorů pro dotazování a převodem těchto výrazů.  
  
 Existuje mnoho standardních dotazovacích operátorů LINQ, které nemají platný překlad v technologii LINQ to Entities. Pokusy o použití těchto operátorů způsobí výjimku v době zpracování dotazu překladu. Seznam podporovaných LINQ to Entities operátory najdete v tématu [podporované a nepodporované metody LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md).  
  
 Další informace o použití standardních operátorů pro dotazování v technologii LINQ to Entities, naleznete v tématu [standardní operátory dotazu v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md).  
  
 Obecně platí výrazy v technologii LINQ to Entities jsou vyhodnoceny na serveru, takže chování výraz neměli očekávat, postupujte podle sémantiky CLR. Další informace najdete v tématu [výrazy v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md).  
  
 Informace o volání metody CLR zpřístupněných kanonické funkce ve zdroji dat, naleznete v tématu [metoda CLR pro mapování kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
 Informace o tom, jak volat canonical, databáze a vlastní funkce v rámci [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy, naleznete v tématu [volání funkcí v dotazech LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md).  
  
## <a name="query-execution"></a>Provádění dotazů  
 Po vytvoření LINQ dotaz tímto uživatelem, je převedena na reprezentaci, jež je kompatibilní s rozhraním Entity Framework (ve formě stromů příkazů), který se potom provede na zdroj dat. V době spuštění dotazu jsou vyhodnoceny všechny výrazy dotazů (nebo součásti dotazu) na straně klienta nebo na serveru. To zahrnuje výrazy, které se používají v materializace výsledek nebo projekce entity. Další informace najdete v tématu [provádění dotazu](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md). Informace o tom, jak zlepšit výkon dotazu kompilace jednou a pak ho spustíte několikrát s různými parametry najdete v tématu [zkompilován dotazy (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).  
  
## <a name="materialization"></a>Materializace  
 Materializace je proces vrácení výsledků dotazu zpět do klienta jako typy CLR. V technologii LINQ to Entities se nikdy vrácena záznamů dat výsledků dotazu. je vždy základní typ CLR, definované uživatelem nebo rozhraním Entity Framework, nebo generovaný kompilátorem (anonymní typy). Všechny materializace objektů se provádí pomocí Entity Frameworku. Všechny chyby, které jsou výsledkem nemožností mapování mezi rozhraním Entity Framework a modulu CLR způsobí, že výjimky, která je vyvolána během materializace objektů.  
  
 Výsledky dotazu jsou obvykle vráceny jako jeden z následujících akcí:  
  
-   Kolekce nulu nebo více objektů zadané entity nebo projekce komplexní typy definované v konceptuálním modelu.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Známé problémy a aspekty u LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
- [Language-Integrated Query (LINQ) –C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Language-Integrated Query (LINQ) – Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ a ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
