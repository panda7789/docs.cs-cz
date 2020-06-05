---
title: Povolení zdroje dat pro LINQ Querying2
ms.date: 07/20/2015
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
ms.openlocfilehash: 4ab0e2a2fc3d04eb375a4646e4133e6e5cbb47db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375301"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Povolení zdroje dat pro dotazy LINQ

Existují různé způsoby, jak technologii LINQ rozšiřuje, aby bylo možné do vzoru LINQ zadat dotaz na libovolný zdroj dat. Zdrojem dat může být kromě jiného například datová struktura, webová služba, systém souborů nebo databáze. Vzor LINQ usnadňuje klientům dotazování na zdroj dat, pro který je povoleno dotazování LINQ, protože syntaxe a vzor dotazu se nezmění. Způsob, jakým lze rozšířit LINQ na tyto zdroje dat, jsou následující:

- Implementace <xref:System.Collections.Generic.IEnumerable%601> rozhraní v typu, aby bylo možné LINQ to Objects dotazování daného typu.

- Vytváření metod standardního operátoru dotazu, jako je <xref:System.Linq.Enumerable.Where%2A> a <xref:System.Linq.Enumerable.Select%2A> které rozšiřuje typ, pro povolení vlastního dotazování LINQ na tento typ.

- Vytvoření poskytovatele pro zdroj dat, který implementuje <xref:System.Linq.IQueryable%601> rozhraní. Zprostředkovatel, který implementuje toto rozhraní, přijímá dotazy LINQ ve formě stromů výrazů, které mohou být spouštěny vlastním způsobem, například vzdáleně.

- Vytvořením zprostředkovatele pro zdroj dat, který využívá stávající technologii LINQ. Takový zprostředkovatel umožní nejen dotazování, ale také operace vložení, aktualizace a odstranění a mapování pro typy definované uživatelem.

Těmito možnostmi se zabývá toto téma.

## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Jak povolit dotazování LINQ na vaše zdroje dat

### <a name="in-memory-data"></a>Data v paměti
 Existují dva způsoby, jak můžete povolit dotazování LINQ na data v paměti. Pokud jsou data typu, který implementuje <xref:System.Collections.Generic.IEnumerable%601> , můžete zadávat dotazy na data pomocí LINQ to Objects. Pokud nemá smysl povolit výčet typu implementací <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete definovat metody operátoru dotazu LINQ standard v tomto typu nebo vytvořit metody operátoru dotazu LINQ Standard, které tento typ rozšiřuje. Vlastní implementace standardních dotazovacích operátorů musí vracet výsledky pomocí odloženého provedení.

### <a name="remote-data"></a>Vzdálená Data
 Nejlepší možností, jak povolit dotazování LINQ na vzdálený zdroj dat, je implementovat <xref:System.Linq.IQueryable%601> rozhraní. To se ale liší od rozšíření poskytovatele, jako je třeba [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] pro zdroj dat. V aplikaci Visual Studio 2008 nejsou k dispozici žádné modely poskytovatele pro rozšíření stávajících technologií LINQ, jako [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] je například, na jiné typy zdrojů dat.

## <a name="iqueryable-linq-providers"></a>Zprostředkovatelé IQueryable LINQ
 Poskytovatelé LINQ implementující se <xref:System.Linq.IQueryable%601> můžou výrazně lišit v jejich složitosti. Tato část pojednává o různých úrovních složitosti.

 Méně komplexní `IQueryable` Poskytovatel může rozhraní používat jedinou metodou webové služby. Tento typ zprostředkovatele je velmi specifický, protože v dotazech, které zpracovává, očekává konkrétní informace. Má uzavřený systém typů, pravděpodobně vystavující jeden typ výsledku. Většina spuštění dotazu probíhá místně, například pomocí <xref:System.Linq.Enumerable> implementací standardních operátorů dotazu. Méně složitý zprostředkovatel může ve stromu výrazů zkoumat pouze jeden výraz volání metody, který představuje dotaz, a nechat zbývající logiku dotazu zpracovat jinde.

 `IQueryable`Poskytovatel střední složitosti může cílit na zdroj dat, který má částečně expresně dotazovací jazyk. Pokud je zaměřena Webová služba, může spolupracovat s více než jednou metodu Webové služby a vybrat metodu volání na základě otázky, kterou dotaz představuje. Zprostředkovatel střední složitosti by měl bohatší systém typů než jednoduchý zprostředkovatel, ale stále by šlo o pevný systému typů. Zprostředkovatel například může vystavit typy, které mají relace typu jeden na mnoho, jež lze procházet, ale neposkytuje technologii mapování pro typy definované uživatelem.

 Komplexní `IQueryable` poskytovatel, jako je například [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] poskytovatel, může překládat kompletní dotazy LINQ na dotazovací jazyk, jako je například SQL. Složitý zprostředkovatel je obecnější než méně složitý zprostředkovatel, protože je v dotazu schopen zpracovávat širší paletu otázek. Rovněž má otevřený systém typů, a proto musí obsahovat rozsáhlou infrastrukturu k mapování typů definovaných uživatelem. Vývoj složitého zprostředkovatele vyžaduje značné úsilí.

## <a name="see-also"></a>Viz také

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Přehled standardních operátorů dotazů (Visual Basic)](standard-query-operators-overview.md)
- [LINQ to Objects (Visual Basic)](linq-to-objects.md)
