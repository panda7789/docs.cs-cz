---
title: Povolení zdroje dat pro LINQ Querying1
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: 5b67995f40bc0cb703003aa80b511268f21da8b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339693"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Povolení zdroje dat pro dotazy LINQ
Existují různé způsoby, jak rozšířit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] povolit jakýkoli zdroj dat do být dotazována v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] vzor. Zdrojem dat může být kromě jiného například datová struktura, webová služba, systém souborů nebo databáze. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Vzor usnadňuje klientům dotazy zdroj dat pro kterou [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování je povolená, protože se syntaxe a vzor dotazu se nemění. Způsoby, ve kterém [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] lze rozšířit pro tyto datové zdroje zahrnují následující:  
  
-   Implementace <xref:System.Collections.Generic.IEnumerable%601> rozhraní v typu Povolit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] k dotazování objekty daného typu.  
  
-   Vytváření dotazu na standardní operátor metody, jako <xref:System.Linq.Enumerable.Where%2A> a <xref:System.Linq.Enumerable.Select%2A> , rozšířit typu, chcete-li povolit vlastní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování daného typu.  
  
-   Vytvoření zprostředkovatele pro zdroj dat, který implementuje <xref:System.Linq.IQueryable%601> rozhraní. Obdrží zprostředkovatele, který toto rozhraní implementuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů ve formě stromů výrazů, které se může spustit vlastním způsobem, například vzdáleně.  
  
-   Vytvoření zprostředkovatele pro zdroj dat, která využívá existující [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] technologie. Takový zprostředkovatel umožní nejen dotazování, ale také operace vložení, aktualizace a odstranění a mapování pro typy definované uživatelem.  
  
 Těmito možnostmi se zabývá toto téma.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Jak povolit dotazování LINQ na vaše zdroje dat  
  
### <a name="in-memory-data"></a>Data v paměti  
 Existují dva způsoby, můžete povolit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování na data v paměti. Pokud je datový typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>, data můžete dotazovat pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] k objektům. Pokud ji nemá smysl povolit výčet typu vašeho implementací <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete definovat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardní dotaz operátor metody v tomto typu nebo vytvořte [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] metody operátor standardní dotazů, které rozšiřují typ. Vlastní implementace standardních dotazovacích operátorů musí vracet výsledky pomocí odloženého provedení.  
  
### <a name="remote-data"></a>Vzdálená Data  
 Nejlepší možnost pro povolení [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování vzdálený zdroj dat je implementace <xref:System.Linq.IQueryable%601> rozhraní. Ale to se liší od zprostředkovatele rozšíření, jako [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] pro zdroj dat. Žádné modely zprostředkovatele pro rozšíření stávající [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] technologií, jako například [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], do jiné typy zdroje dat jsou k dispozici v [!INCLUDE[vs_orcas_long](~/includes/vs-orcas-long-md.md)].  
  
## <a name="iqueryable-linq-providers"></a>Zprostředkovatelé IQueryable LINQ  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zprostředkovatelé, kteří implementují <xref:System.Linq.IQueryable%601> se v jejich složitost může výrazně lišit. Tato část pojednává o různých úrovních složitosti.  
  
 Menší komplexní `IQueryable` zprostředkovatele může rozhraní s jedné metody webové služby. Tento typ zprostředkovatele je velmi specifický, protože v dotazech, které zpracovává, očekává konkrétní informace. Má uzavřený systém typů, pravděpodobně vystavující jeden typ výsledku. Většina spuštění dotazu nastane místně, například pomocí <xref:System.Linq.Enumerable> implementace standardní operátory dotazu. Méně složitý zprostředkovatel může ve stromu výrazů zkoumat pouze jeden výraz volání metody, který představuje dotaz, a nechat zbývající logiku dotazu zpracovat jinde.  
  
 `IQueryable` Zprostředkovatele střední složitost může cíle zdroj dat, který má částečně výrazovou dotazovací jazyk. Pokud je zaměřena Webová služba, může spolupracovat s více než jednou metodu Webové služby a vybrat metodu volání na základě otázky, kterou dotaz představuje. Zprostředkovatel střední složitosti by měl bohatší systém typů než jednoduchý zprostředkovatel, ale stále by šlo o pevný systému typů. Zprostředkovatel například může vystavit typy, které mají relace typu jeden na mnoho, jež lze procházet, ale neposkytuje technologii mapování pro typy definované uživatelem.  
  
 Komplexní `IQueryable` poskytovatele, například [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] poskytovatele, může překládat dokončení [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů výrazovou dotazovací jazyk, jako je například SQL. Složitý zprostředkovatel je obecnější než méně složitý zprostředkovatel, protože je v dotazu schopen zpracovávat širší paletu otázek. Rovněž má otevřený systém typů, a proto musí obsahovat rozsáhlou infrastrukturu k mapování typů definovaných uživatelem. Vývoj složitého zprostředkovatele vyžaduje značné úsilí.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.IQueryable%601>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 <xref:System.Linq.Enumerable>  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [LINQ na objekty (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
