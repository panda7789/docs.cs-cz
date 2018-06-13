---
title: join – klauzule (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- join
- join_CSharpKeyword
helpviewer_keywords:
- join clause [C#]
- join keyword [C#]
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
ms.openlocfilehash: a868c52cf753b1e4285586ec41c1993f519299d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289396"
---
# <a name="join-clause-c-reference"></a>join – klauzule (Referenční dokumentace jazyka C#)
`join` Klauzule je užitečné pro přidružení elementy z jiné zdrojové pořadí, které nemají přímé relaci v objektu modelu. Jediným požadavkem je, že elementů v jednotlivých zdrojů sdílet určitou hodnotu, která může být porovnána shoda. Například distributora jídlo může mít seznam dodavatelé určité produktu a seznamu odběratelů. A `join` klauzuli lze použít, například můžete vytvořit seznam dodavatelů a zadané odběratelů tohoto produktu, kteří jsou ve stejné oblasti.  
  
 A `join` klauzule přebírá dva pořadí zdroj jako vstup. Prvky v každé pořadí musí být buď nebo obsahovat vlastnosti, která lze porovnat s hodnotou pro odpovídající vlastnost v jiných pořadí. `join` Klauzule porovná zadanými klíči rovnosti pomocí speciální `equals` – klíčové slovo. Všechny spojení provádí `join` klauzule jsou equijoins. Obrazec výstup `join` klauzule závisí na konkrétní typ připojení k provádění. Tady jsou tři nejběžnější typy připojení:  
  
-   vnitřní spojení  
  
-   Připojení skupiny  
  
-   Levé vnější spojení  
  
## <a name="inner-join"></a>Vnitřní spojení  
 Následující příklad ukazuje jednoduchý vnitřní porovnávání. Tento dotaz vytváří ploché posloupnost "název produktu nebo kategorie" páry. Do jednoho řetězce kategorie se zobrazí v více elementů. Pokud element z `categories` má neexistuje odpovídající `products`, této kategorie se nezobrazí ve výsledcích.  
  
 [!code-csharp[cscsrefQueryKeywords#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_1.cs)]  
  
 Další informace najdete v tématu [postup: provedení vnitřní spojení](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md).  
  
## <a name="group-join"></a>Group Join  
 A `join` klauzuli with `into` výraz se nazývá skupina spojení.  
  
 [!code-csharp[cscsrefQueryKeywords#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_2.cs)]  
  
 Skupiny připojení vytvoří pořadí hierarchických výsledek, který přidruží jeden či více elementů odpovídající pravé straně zdrojové sekvence elementy v levém zdrojové sekvence. Připojení skupiny nemá žádný ekvivalent v relační podmínky; je v podstatě posloupnost pole objektů.  
  
 Pokud se nenajdou žádné elementy z pravé zdrojové sekvence tak, aby odpovídaly element ve zdroji levém `join` klauzule vytvoří prázdné pole pro tuto položku. Proto spojení skupiny je stále v podstatě vnitřní porovnávání s tím rozdílem, že pořadí výsledek je uspořádaných do skupin.  
  
 Pokud vyberete jenom výsledky spojení skupiny, můžete přístup k položkám, ale nemůže identifikovat klíč, který budou odpovídat na. Proto je obecně vzato užitečnější vyberte výsledky spojení skupiny do nový typ, který má také název klíče, jak je znázorněno v předchozím příkladu.  
  
 Navíc samozřejmě můžete výsledek spojení skupiny jako generátor jiné poddotazu:  
  
 [!code-csharp[cscsrefQueryKeywords#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_3.cs)]  
  
 Další informace najdete v tématu [postupy: provádění seskupených spojení](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md).  
  
## <a name="left-outer-join"></a>Levého vnějšího spojení  
 V levé vnější spojení jsou vráceny všechny elementy v levém zdrojové sekvence, i když žádné odpovídající elementy jsou v pravém pořadí. Účelem levé vnější spojení v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], použijte `DefaultIfEmpty` metoda v kombinaci s skupiny připojení zadat výchozí pravé straně element k vytvoření, pokud na levé straně element má žádné odpovídající položky. Můžete použít `null` jako výchozí hodnota pro všechny odkazy typu nebo můžete zadat vlastní výchozí typ. V následujícím příkladu se zobrazí uživatelské výchozí typ:  
  
 [!code-csharp[cscsrefQueryKeywords#27](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_4.cs)]  
  
 Další informace najdete v tématu [postup: provedení vnější spojení levé](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md).  
  
## <a name="the-equals-operator"></a>Operátor je rovno  
 A `join` klauzule provádí porovnávání. Jinými slovy můžete pouze základní odpovídá na rovnosti dvou klíčů. Jiné typy porovnání například "větší než" nebo "není rovno" nejsou podporovány. Aby se vyjasnilo, že jsou všechna spojení equijoins, `join` používá klauzule `equals` – klíčové slovo místo `==` operátor. `equals` – Klíčové slovo lze použít pouze v `join` klauzule a se liší od `==` operátor jedním způsobem důležité. S `equals`levé klíč spotřebovává vnější zdrojové sekvence a pravé klávesy využívá vnitřní zdroj. Vnější zdroj nachází pouze v oboru na levé straně `equals` a vnitřní zdrojové sekvence je pouze v oboru na pravé straně.  
  
## <a name="non-equijoins"></a>Bez Equijoins  
 Můžete nastavit jiný equijoins, křížové spojení a dalších vlastních operací spojování pomocí několika `from` klauzule zavést nové pořadí nezávisle do dotazu. Další informace najdete v tématu [postup: provedení vlastní připojení Operations](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).  
  
## <a name="joins-on-object-collections-vs-relational-tables"></a>Spojení na kolekce objektů oproti relační tabulky  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazu dotazu, spojení operací na kolekce objektů. Objekt kolekce se nedá "připojit" přesně stejným způsobem jako relační dvě tabulky. V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], explicitní `join` klauzule jsou pouze při dvě zdrojové sekvence nejsou svázané žádné vztahem vyžaduje. Při práci s [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], cizí klíče tabulky jsou vyjádřené v modelu objektu vlastnosti v primární tabulce. V databázi Northwind, například tabulky Zákazník má relace cizího klíče s tabulkou objednávky. Při mapování tabulek do objektu modelu, třídu Customer má vlastnost objednávky, která obsahuje kolekci objednávky spojené s tohoto zákazníka. Ve skutečnosti spojení již byla provedl za vás.  
  
 Další informace o dotazování napříč související tabulky v kontextu [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], najdete v části [postup: mapy databáze vztahy](../../../framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
## <a name="composite-keys"></a>Složené klíče  
 Rovnosti obsahující více hodnot můžete otestovat pomocí složeného klíče. Další informace najdete v tématu [postupy: spojení pomocí složených klíčů pomocí](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md). Složené klíče mohou být také používány `group` klauzule.  
  
## <a name="example"></a>Příklad  
 Následující příklad porovná výsledky vnitřní spojení, skupiny spojení a levé vnější spojení na stejném zdroji dat pomocí stejné odpovídající klíče. Některé další kód se přidá na tyto příklady o vysvětlení, výsledky v zobrazení konzoly.  
  
 [!code-csharp[cscsrefQueryKeywords#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/join-clause_5.cs)]  
  
## <a name="remarks"></a>Poznámky  
 A `join` klauzuli, která není následuje `into` je přeložit na <xref:System.Linq.Enumerable.Join%2A> volání metody. A `join` klauzuli, která následuje `into` převádějí na <xref:System.Linq.Enumerable.GroupJoin%2A> volání metody.  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova dotazu (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Operace sjednocení](../../programming-guide/concepts/linq/join-operations.md)  
 [group – klauzule](../../../csharp/language-reference/keywords/group-clause.md)  
 [Postup: provedení levých vnějších spojení](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)  
 [Postupy: provádění vnitřních spojení](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)  
 [Postupy: provádění seskupených spojení](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)  
 [Postupy: řazení výsledků Klauzule Join](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [Postupy: spojení pomocí složených klíčů](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)  
 [Postupy: Instalace ukázkových databází](/visualstudio/data-tools/installing-database-systems-tools-and-samples)
