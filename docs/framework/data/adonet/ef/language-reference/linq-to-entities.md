---
title: LINQ to Entities
description: Naučte se vytvářet a spouštět dotazy LINQ to Entities, které umožňují psát dotazy pro Entity Framework koncepční model pomocí Visual Basic nebo Visual C#.
ms.date: 03/30/2017
ms.assetid: 641f9b68-9046-47a1-abb0-1c8eaeda0e2d
ms.openlocfilehash: 389a81872f4652c69e2b845359cf4e5a275aed5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286841"
---
# <a name="linq-to-entities"></a>LINQ to Entities
LINQ to Entities poskytuje podporu LINQ (Language-Integrated Query), která umožňuje vývojářům psát dotazy pro Entity Framework koncepční model pomocí Visual Basic nebo Visual C#. Dotazy na Entity Framework jsou reprezentovány pomocí příkazového stromu příkazů, které jsou spouštěny proti kontextu objektu. LINQ to Entities převede dotazy na dotazy integrované v jazyce (LINQ) na dotazy stromu příkazů, spustí dotazy proti Entity Framework a vrátí objekty, které mohou být použity Entity Framework i LINQ. Následující postup slouží k vytvoření a spuštění dotazu LINQ to Entities:  
  
1. Vytvořte <xref:System.Data.Objects.ObjectQuery%601> instanci z <xref:System.Data.Objects.ObjectContext> .  
  
2. Vytvoření dotazu LINQ to Entities v jazyce C# nebo Visual Basic pomocí <xref:System.Data.Objects.ObjectQuery%601> instance.  
  
3. Převede operátory dotazů LINQ Standard a výrazy na stromy příkazů.  
  
4. Spusťte dotaz, v reprezentace stromu příkazů, oproti zdroji dat. Jakékoli výjimky vyvolané ve zdroji dat během provádění jsou předány přímo do klienta.  
  
5. Vrátí výsledky dotazu zpátky klientovi.  
  
## <a name="constructing-an-objectquery-instance"></a>Sestavování instance ObjectQuery  
 <xref:System.Data.Objects.ObjectQuery%601>Obecná třída reprezentuje dotaz, který vrací kolekci nula nebo více typových entit. Dotaz na objekt je obvykle vytvořen z kontextu existujícího objektu místo ručního sestavení a vždy patří do kontextu daného objektu. Tento kontext poskytuje informace o připojení a metadatech, které jsou nutné k vytvoření a spuštění dotazu. <xref:System.Data.Objects.ObjectQuery%601>Obecná třída implementuje <xref:System.Linq.IQueryable%601> Obecné rozhraní, jejichž metody Tvůrce umožňují přírůstkové sestavení dotazů LINQ. Můžete také nechat kompilátor odvodit typ entit pomocí `var` klíčového slova jazyka C# ( `Dim` v Visual Basic s povoleným odvozením místního typu).  
  
## <a name="composing-the-queries"></a>Vytváření dotazů  
 Instance <xref:System.Data.Objects.ObjectQuery%601> Obecné třídy, které implementují obecné <xref:System.Linq.IQueryable%601> rozhraní, slouží jako zdroj dat pro LINQ to Entities dotazů. V dotazu zadáte přesně informace, které chcete načíst ze zdroje dat. Dotaz může také určit, jak se mají tyto informace seřadit, seskupit a tvarovat před tím, než se vrátí. V LINQ je dotaz uložen v proměnné. Tato proměnná dotazu neprovádí žádnou akci a nevrátí žádná data. ukládá pouze informace o dotazu. Po vytvoření dotazu musíte spustit dotaz, aby se načetla nějaká data.  
  
 Dotazy LINQ to Entities můžou být složené ve dvou různých syntaxech: syntax výrazů dotazů a syntaxe dotazů založených na metodách. Syntaxe výrazu dotazu a syntaxe dotazu založeného na metodách jsou v jazyce C# 3,0 a Visual Basic 9,0 novinkou.  
  
 Další informace najdete v tématu [dotazy v LINQ to Entities](queries-in-linq-to-entities.md).  
  
## <a name="query-conversion"></a>Převod dotazů  
 Chcete-li spustit dotaz LINQ to Entities proti Entity Framework, je nutné dotaz LINQ převést na reprezentace stromu příkazů, která může být provedena proti Entity Framework.  
  
 LINQ to Entities dotazy se skládají z standardních operátorů dotazů LINQ (například <xref:System.Linq.Queryable.Select%2A> , <xref:System.Linq.Queryable.Where%2A> a <xref:System.Linq.Queryable.GroupBy%2A> ) a výrazů (x > 10, Contact. LastName atd.). Operátory LINQ nejsou definovány třídou, ale spíše jsou metody třídy. Výrazy v jazyce LINQ mohou obsahovat cokoli, co povoluje typy v rámci <xref:System.Linq.Expressions> oboru názvů a podle přípony, cokoli, co může být reprezentována ve funkci lambda. Toto je nadmnožina výrazů, které jsou povoleny Entity Framework, které jsou podle definice omezené na operace povolené v databázi a které podporuje <xref:System.Data.Objects.ObjectQuery%601> .  
  
 V Entity Framework jsou oba operátory a výrazy zastoupeny jedinou hierarchií typů, která je poté umístěna do stromu příkazů. Strom příkazů je používán Entity Framework k provedení dotazu. Pokud dotaz LINQ nelze vyjádřit jako strom příkazů, při převodu dotazu bude vyvolána výjimka. Převod LINQ to Entities dotazů zahrnuje dva dílčí převody: převod standardních operátorů dotazu a převod výrazů.  
  
 Existuje mnoho standardních operátorů dotazů LINQ, které nemají platný překlad v LINQ to Entities. Pokusy o použití těchto operátorů způsobí výjimku v době překladu dotazů. Seznam podporovaných operátorů LINQ to Entities najdete v tématu [podporované a nepodporované metody LINQ (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md).  
  
 Další informace o použití standardních operátorů dotazu v LINQ to Entities naleznete v tématu [standardní operátory dotazu v LINQ to Entitiesch dotazech](standard-query-operators-in-linq-to-entities-queries.md).  
  
 Obecně platí, že výrazy ve LINQ to Entities jsou vyhodnocovány na serveru, takže chování výrazu by nemělo následovat za sémantikou CLR. Další informace najdete v tématu [výrazy v LINQ to Entitiesch dotazech](expressions-in-linq-to-entities-queries.md).  
  
 Informace o tom, jak jsou volání metod CLR mapována na kanonické funkce ve zdroji dat, naleznete v tématu [Metoda CLR na kanonické mapování funkcí](clr-method-to-canonical-function-mapping.md).  
  
 Informace o tom, jak volat kanonické, databázové a vlastní funkce v rámci LINQ to Entitiesch dotazů, najdete v tématu [volání funkcí v dotazech LINQ to Entities](calling-functions-in-linq-to-entities-queries.md).  
  
## <a name="query-execution"></a>Provádění dotazů  
 Poté, co uživatel vytvoří dotaz LINQ, je převedena na reprezentace, která je kompatibilní s Entity Framework (ve formě stromů příkazů), který je následně proveden proti zdroji dat. V době spuštění dotazu jsou všechny výrazy dotazu (nebo komponenty dotazu) vyhodnocovány na klientovi nebo na serveru. To zahrnuje výrazy, které se používají v materializech výsledků nebo projektech entit. Další informace najdete v tématu [provádění dotazů](query-execution.md). Informace o tom, jak zvýšit výkon kompilováním dotazu jednou a jeho spuštěním několikrát s různými parametry, naleznete v tématu [kompilované dotazy (LINQ to Entities)](compiled-queries-linq-to-entities.md).  
  
## <a name="materialization"></a>Materializaci  
 Materializace je proces vrácení výsledků dotazu zpět do klienta jako typy CLR. V LINQ to Entities se záznamy dat výsledků dotazu nikdy nevrátí; vždy je k dispozici záložní typ CLR definovaný uživatelem nebo Entity Framework nebo generovaný kompilátorem (anonymní typy). Všechny materializování objektů provádí Entity Framework. Všechny chyby, které jsou výsledkem neschopnosti mapování mezi Entity Framework a CLR, způsobí, že budou výjimky vyvolány během materializace objektu.  
  
 Výsledky dotazu jsou obvykle vraceny jako jedna z následujících:  
  
- Kolekce nula nebo více typových objektů entit nebo projekce komplexních typů definovaných v koncepčním modelu.  
  
- Typy CLR, které jsou podporovány Entity Framework.  
  
- Vložené kolekce.  
  
- Anonymní typy.  
  
 Další informace najdete v tématu [výsledky dotazu](query-results.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Dotazy v technologii LINQ to Entities](queries-in-linq-to-entities.md)  
  
 [Výrazy v dotazech LINQ to Entities](expressions-in-linq-to-entities-queries.md)  
  
 [Volání funkcí v dotazech LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)  
  
 [Kompilované dotazy (LINQ to Entities)](compiled-queries-linq-to-entities.md)  
  
 [Provádění dotazů](query-execution.md)  
  
 [Výsledky dotazu](query-results.md)  
  
 [Standardní operátory dotazů LINQ to Entities](standard-query-operators-in-linq-to-entities-queries.md)  
  
 [Metoda CLR pro mapování kanonických funkcí](clr-method-to-canonical-function-mapping.md)  
  
 [Podporované a nepodporované metody LINQ (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md)  
  
 [Známé problémy a aspekty u LINQ to Entities](known-issues-and-considerations-in-linq-to-entities.md)  
  
## <a name="see-also"></a>Viz také

- [Známé problémy a aspekty u LINQ to Entities](known-issues-and-considerations-in-linq-to-entities.md)
- [LINQ (Language-Integrated Query)-C #](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (Language-Integrated Query) – Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ a ADO.NET](../../linq-and-ado-net.md)
- [ADO.NET Entity Framework](../index.md)
