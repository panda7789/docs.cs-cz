---
title: Povolení zdroje dat pro LINQ Querying2
ms.date: 07/20/2015
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
ms.openlocfilehash: 312a880158e4d9254d6ead81538dc9a17e5c31b0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "68959789"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Povolení zdroje dat pro dotazy LINQ

Existují různé způsoby, jak se [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dá zvětšit, aby bylo možné do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] vzoru zadat dotaz na libovolný zdroj dat. Zdrojem dat může být kromě jiného například datová struktura, webová služba, systém souborů nebo databáze. Vzor usnadňuje klientům dotazování na zdroj dat, pro který [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] je povoleno dotazování, protože syntaxe a vzor dotazu se nezmění. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Způsob, jakým [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] lze rozšířit na tyto zdroje dat, jsou následující:

- Implementace rozhraní v typu, který umožňuje objektům dotazovat se [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] na daný typ. <xref:System.Collections.Generic.IEnumerable%601>

- Vytváření metod standardního operátoru dotazu, <xref:System.Linq.Enumerable.Where%2A> jako <xref:System.Linq.Enumerable.Select%2A> je a které rozšiřuje typ, pro povolení [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] vlastního dotazování na daný typ.

- Vytvoření poskytovatele pro zdroj dat, který implementuje <xref:System.Linq.IQueryable%601> rozhraní. Zprostředkovatel, který implementuje toto rozhraní, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] přijímá dotazy ve formě stromů výrazů, které mohou být spouštěny vlastním způsobem, například vzdáleně.

- Vytvoření zprostředkovatele pro zdroj dat, který využívá stávající [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] technologii. Takový zprostředkovatel umožní nejen dotazování, ale také operace vložení, aktualizace a odstranění a mapování pro typy definované uživatelem.

Těmito možnostmi se zabývá toto téma.

## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Jak povolit dotazování LINQ na vaše zdroje dat

### <a name="in-memory-data"></a>Data v paměti
 Existují dva způsoby, jak můžete povolit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování na data v paměti. Pokud jsou data typu, který implementuje <xref:System.Collections.Generic.IEnumerable%601>, můžete zadávat dotazy na data pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] objektů. Pokud nemá smysl povolit výčet typu implementací <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete definovat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardní metody operátoru dotazu v tomto typu nebo vytvořit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardní metody operátoru dotazu, které tento typ rozšiřuje. Vlastní implementace standardních dotazovacích operátorů musí vracet výsledky pomocí odloženého provedení.

### <a name="remote-data"></a>Vzdálená Data
 Nejlepší možností, jak povolit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování vzdáleného zdroje dat, je <xref:System.Linq.IQueryable%601> implementovat rozhraní. To se ale liší od rozšíření poskytovatele, jako je třeba [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] pro zdroj dat. V aplikaci Visual Studio 2008 nejsou [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] k dispozici žádné [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]modely poskytovatele pro rozšíření stávajících technologií, například k jiným typům zdrojů dat.

## <a name="iqueryable-linq-providers"></a>Zprostředkovatelé IQueryable LINQ
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]poskytovatelé, <xref:System.Linq.IQueryable%601> kteří implementují, se můžou výrazně lišit v jejich složitosti. Tato část pojednává o různých úrovních složitosti.

 Méně komplexní `IQueryable` poskytovatel může rozhraní používat jedinou metodou webové služby. Tento typ zprostředkovatele je velmi specifický, protože v dotazech, které zpracovává, očekává konkrétní informace. Má uzavřený systém typů, pravděpodobně vystavující jeden typ výsledku. Většina spuštění dotazu probíhá místně, například pomocí <xref:System.Linq.Enumerable> implementací standardních operátorů dotazu. Méně složitý zprostředkovatel může ve stromu výrazů zkoumat pouze jeden výraz volání metody, který představuje dotaz, a nechat zbývající logiku dotazu zpracovat jinde.

 `IQueryable` Poskytovatel střední složitosti může cílit na zdroj dat, který má částečně expresně dotazovací jazyk. Pokud je zaměřena Webová služba, může spolupracovat s více než jednou metodu Webové služby a vybrat metodu volání na základě otázky, kterou dotaz představuje. Zprostředkovatel střední složitosti by měl bohatší systém typů než jednoduchý zprostředkovatel, ale stále by šlo o pevný systému typů. Zprostředkovatel například může vystavit typy, které mají relace typu jeden na mnoho, jež lze procházet, ale neposkytuje technologii mapování pro typy definované uživatelem.

 Komplexní `IQueryable` poskytovatel, jako je [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] například poskytovatel, může překládat kompletní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy na dotazovací jazyk, jako je například SQL. Složitý zprostředkovatel je obecnější než méně složitý zprostředkovatel, protože je v dotazu schopen zpracovávat širší paletu otázek. Rovněž má otevřený systém typů, a proto musí obsahovat rozsáhlou infrastrukturu k mapování typů definovaných uživatelem. Vývoj složitého zprostředkovatele vyžaduje značné úsilí.

## <a name="see-also"></a>Viz také:

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Přehled standardních operátorů dotazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
