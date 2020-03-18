---
title: Povolení zdroje dat pro dotazy LINQ
ms.date: 07/20/2015
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
ms.openlocfilehash: 9a143f0da74d4e91ef697f468d7fda225e75245b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635766"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Povolení zdroje dat pro dotazy LINQ
Existují různé způsoby, jak rozšířit LINQ povolit libovolný zdroj dat, které mají být dotazovány ve vzoru LINQ. Zdrojem dat může být kromě jiného například datová struktura, webová služba, systém souborů nebo databáze. Linq vzor usnadňuje klientům dotaz na zdroj dat, pro které linq dotazování je povolena, protože syntaxe a vzor dotazu se nemění. Způsoby, kterými linq lze rozšířit na tyto zdroje dat patří následující:  
  
- Implementace <xref:System.Collections.Generic.IEnumerable%601> rozhraní v typu povolit LINQ na objekty dotazování tohoto typu.  
  
- Vytvoření standardní metody operátor <xref:System.Linq.Enumerable.Where%2A> <xref:System.Linq.Enumerable.Select%2A> dotazu, jako je například a které rozšiřují typ, aby vlastní LINQ dotazování tohoto typu.  
  
- Vytvoření zprostředkovatele pro zdroj dat, <xref:System.Linq.IQueryable%601> který implementuje rozhraní. Zprostředkovatel, který implementuje toto rozhraní obdrží LINQ dotazy ve formě stromů výrazů, které lze spustit vlastním způsobem, například vzdáleně.  
  
- Vytvoření zprostředkovatele pro váš zdroj dat, který využívá existující technologii LINQ. Takový zprostředkovatel umožní nejen dotazování, ale také operace vložení, aktualizace a odstranění a mapování pro typy definované uživatelem.  
  
 Těmito možnostmi se zabývá toto téma.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Jak povolit dotazování LINQ na vaše zdroje dat  
  
### <a name="in-memory-data"></a>Data v paměti  
 Existují dva způsoby, jak můžete povolit linq dotazování dat v paměti. Pokud data je typu, který <xref:System.Collections.Generic.IEnumerable%601>implementuje , můžete dotaz na data pomocí LINQ na objekty. Pokud nemá smysl povolit výčet typu implementací <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete definovat metody standardního operátoru dotazu LINQ v tomto typu nebo vytvořit metody standardního operátoru dotazu LINQ, které tento typ rozšiřují. Vlastní implementace standardních dotazovacích operátorů musí vracet výsledky pomocí odloženého provedení.  
  
### <a name="remote-data"></a>Vzdálená Data  
 Nejlepší možností pro povolení linq dotazování vzdáleného zdroje <xref:System.Linq.IQueryable%601> dat je implementovat rozhraní. To se však liší od rozšíření [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zprostředkovatele, například pro zdroj dat. V sadě Visual Studio 2008 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]nejsou k dispozici žádné modely zprostředkovatelů pro rozšíření existujících technologií LINQ, například na jiné typy zdrojů dat.
  
## <a name="iqueryable-linq-providers"></a>Zprostředkovatelé IQueryable LINQ  
 Linq zprostředkovatelé, které implementují <xref:System.Linq.IQueryable%601> se může značně lišit v jejich složitosti. Tato část pojednává o různých úrovních složitosti.  
  
 Méně složitý `IQueryable` zprostředkovatel může komunikovat s jedinou metodou webové služby. Tento typ zprostředkovatele je velmi specifický, protože v dotazech, které zpracovává, očekává konkrétní informace. Má uzavřený systém typů, pravděpodobně vystavující jeden typ výsledku. Většina provádění dotazu probíhá místně, například <xref:System.Linq.Enumerable> pomocí implementace operátorů standardní dotaz. Méně složitý zprostředkovatel může ve stromu výrazů zkoumat pouze jeden výraz volání metody, který představuje dotaz, a nechat zbývající logiku dotazu zpracovat jinde.  
  
 Zprostředkovatel `IQueryable` střední složitosti může cílit na zdroj dat, který má částečně expresivní dotazovací jazyk. Pokud je zaměřena Webová služba, může spolupracovat s více než jednou metodu Webové služby a vybrat metodu volání na základě otázky, kterou dotaz představuje. Zprostředkovatel střední složitosti by měl bohatší systém typů než jednoduchý zprostředkovatel, ale stále by šlo o pevný systému typů. Zprostředkovatel například může vystavit typy, které mají relace typu jeden na mnoho, jež lze procházet, ale neposkytuje technologii mapování pro typy definované uživatelem.  
  
 Komplexní `IQueryable` zprostředkovatel, jako [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] je například zprostředkovatel, může přeložit úplné dotazy LINQ do expresivního dotazovacího jazyka, například SQL. Složitý zprostředkovatel je obecnější než méně složitý zprostředkovatel, protože je v dotazu schopen zpracovávat širší paletu otázek. Rovněž má otevřený systém typů, a proto musí obsahovat rozsáhlou infrastrukturu k mapování typů definovaných uživatelem. Vývoj složitého zprostředkovatele vyžaduje značné úsilí.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
- [LINQ na objekty (C#)](./linq-to-objects.md)
