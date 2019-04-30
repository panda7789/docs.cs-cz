---
title: Povoluje se zdrojem dat pro LINQ Querying2
ms.date: 07/20/2015
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
ms.openlocfilehash: f705db90f4838479621117bd9303f5a374d33d4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781027"
---
# <a name="enabling-a-data-source-for-linq-querying"></a>Povolení zdroje dat pro dotazy LINQ

Existují různé způsoby, jak rozšířit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pro libovolný zdroj dat, aby se dalo dotazovat v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] vzor. Zdrojem dat může být kromě jiného například datová struktura, webová služba, systém souborů nebo databáze. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Vzor usnadňuje klientům dotazování na zdroj dat, pro kterou [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování je povoleno, protože syntaxe a vzor dotazu se nezmění. Způsoby [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] je možné rozšířit na tyto data zdroje patří následující:

- Implementace <xref:System.Collections.Generic.IEnumerable%601> rozhraní v typu, aby [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] mohl dotazovat na objekty tohoto typu.

- Vytváření dotazu na standardní metody operátoru jako <xref:System.Linq.Enumerable.Where%2A> a <xref:System.Linq.Enumerable.Select%2A> , které rozšiřují typ, chcete povolit vlastní [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování daného typu.

- Vytvořením zprostředkovatele zdroje dat, který implementuje <xref:System.Linq.IQueryable%601> rozhraní. Zprostředkovatel, který implementuje toto rozhraní obdrží [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy v podobě stromů výrazů, jež provádí vlastním způsobem, například vzdáleně.

- Vytvořením zprostředkovatele zdroje dat, který využívá existující [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] technologie. Takový zprostředkovatel umožní nejen dotazování, ale také operace vložení, aktualizace a odstranění a mapování pro typy definované uživatelem.

Těmito možnostmi se zabývá toto téma.

## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Jak povolit dotazování LINQ na vaše zdroje dat

### <a name="in-memory-data"></a>Data v paměti
 Existují dva způsoby, jak můžete povolit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování na data v paměti. Pokud jsou data typu, který implementuje <xref:System.Collections.Generic.IEnumerable%601>, můžete dotazovat data pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] na objekty. Pokud ji nemá smysl povolovat výčet typu pomocí implementace <xref:System.Collections.Generic.IEnumerable%601> rozhraní, můžete definovat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardní metody operátoru v tomto typu dotazu nebo vytvoření [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standardní metody operátoru dotazu, které typ rozšiřují. Vlastní implementace standardních dotazovacích operátorů musí vracet výsledky pomocí odloženého provedení.

### <a name="remote-data"></a>Vzdálená Data
 Nejlepší možností pro povolení [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování vzdálený zdroj dat je implementace <xref:System.Linq.IQueryable%601> rozhraní. Ale to se liší od zprostředkovatele rozšíření, jako [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] pro zdroj dat. Žádné modely zprostředkovatelů pro rozšíření stávajících [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] technologií, jako například [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]na jiné typy zdroje dat jsou k dispozici v sadě Visual Studio 2008.

## <a name="iqueryable-linq-providers"></a>Zprostředkovatelé IQueryable LINQ
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] poskytovatelé, které implementují <xref:System.Linq.IQueryable%601> může výrazně lišit složitosti. Tato část pojednává o různých úrovních složitosti.

 Méně složitý `IQueryable` poskytovatele může spolupracovat s jedinou metodu webové služby. Tento typ zprostředkovatele je velmi specifický, protože v dotazech, které zpracovává, očekává konkrétní informace. Má uzavřený systém typů, pravděpodobně vystavující jeden typ výsledku. Provádění dotazu většiny dochází místně, například pomocí <xref:System.Linq.Enumerable> implementace standardních dotazovacích operátorů. Méně složitý zprostředkovatel může ve stromu výrazů zkoumat pouze jeden výraz volání metody, který představuje dotaz, a nechat zbývající logiku dotazu zpracovat jinde.

 `IQueryable` Středně složitý zprostředkovatel může zaměřit zdroj dat, který má částečně výrazový dotazovací jazyk. Pokud je zaměřena Webová služba, může spolupracovat s více než jednou metodu Webové služby a vybrat metodu volání na základě otázky, kterou dotaz představuje. Zprostředkovatel střední složitosti by měl bohatší systém typů než jednoduchý zprostředkovatel, ale stále by šlo o pevný systému typů. Zprostředkovatel například může vystavit typy, které mají relace typu jeden na mnoho, jež lze procházet, ale neposkytuje technologii mapování pro typy definované uživatelem.

 Komplexní `IQueryable` zprostředkovatele, například [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] poskytovatele, může překládat úplné [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy na výrazový dotazovací jazyk, jako je například SQL. Složitý zprostředkovatel je obecnější než méně složitý zprostředkovatel, protože je v dotazu schopen zpracovávat širší paletu otázek. Rovněž má otevřený systém typů, a proto musí obsahovat rozsáhlou infrastrukturu k mapování typů definovaných uživatelem. Vývoj složitého zprostředkovatele vyžaduje značné úsilí.

## <a name="see-also"></a>Viz také:

- <xref:System.Linq.IQueryable%601>
- <xref:System.Collections.Generic.IEnumerable%601>
- <xref:System.Linq.Enumerable>
- [Přehled standardních operátorů dotazu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)