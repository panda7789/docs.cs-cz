---
title: Dotazování napříč relacemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: 1675e4c6a610373e1c981b383ae0229739d96dd0
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003329"
---
# <a name="querying-across-relationships"></a>Dotazování napříč relacemi
Odkazy na jiné objekty nebo kolekce jiných objektů v definicích vaší třídy přímo odpovídají vztahům cizího klíče v databázi. Tyto relace můžete použít při dotazování pomocí zápisu teček pro přístup k vlastnostem vztahu a přechodu z jednoho objektu na jiný. Tyto operace přístupu se převádějí na složitější spojení nebo korelační poddotazy v ekvivalentním SQL.  
  
 Například následující dotaz přechází z objednávek na zákazníky jako způsob, jak omezit výsledky jenom na objednávky pro zákazníky, kteří se nacházejí v Londýně.  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 Pokud vlastnosti vztahu neexistují, musíte je napsat ručně jako *spojení*, stejně jako v dotazu SQL, jako v následujícím kódu:  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 Můžete použít vlastnost *Relationship* k definování tohoto konkrétního vztahu v jednom okamžiku. Pak můžete použít pohodlnější syntaxi teček. Ale vlastnosti vztahu existují důležitější, protože objektové modely specifické pro doménu jsou obvykle definovány jako hierarchie nebo grafy. Objekty, které program mají, mají odkazy na jiné objekty. Je to jenom šťastný výskyt, který vztahy mezi objekty a objekty odpovídají vztahům na základě vztahu cizího klíče v databázích. Přístup k vlastnostem pak poskytuje pohodlný způsob, jak psát spojení.  
  
 Z toho vyplývá, že vlastnosti vztahu jsou důležitější než na straně výsledků dotazu, než jako součást dotazu samotného. Poté, co dotaz načte data o konkrétním zákazníkovi, definice třídy označuje, že zákazníci mají objednávky. Jinými slovy, očekáváte, že vlastnost `Orders` určitého zákazníka bude kolekce, která je vyplněna všemi objednávkami tohoto zákazníka. To je ve skutečnosti kontrakt, který jste deklarovali definováním tříd tímto způsobem. Očekává se, že se zobrazí objednávky i v případě, že dotaz nepožadoval objednávky. Očekáváte, že objektový model udržuje iluzi, že se jedná o příponu v paměti databáze se souvisejícími objekty hned dostupnými.  
  
 Teď, když máte relace, můžete napsat dotazy odkazem na vlastnosti vztahu definované ve vašich třídách. Tyto odkazy na relace odpovídají vztahům cizího klíče v databázi. Operace, které tyto relace používají, se převádějí do složitějších spojení v ekvivalentním kódu SQL. Pokud jste definovali relaci (pomocí atributu <xref:System.Data.Linq.Mapping.AssociationAttribute>), nemusíte v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zakódovat explicitní spojení.  
  
 Pro lepší údržbu této iluze [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje techniku s názvem *odložené načítání*. Další informace najdete v tématu [odložené porovnání a okamžité načítání](deferred-versus-immediate-loading.md).  
  
 Zvažte následující dotaz SQL pro projektování seznamu `CustomerID`-`OrderID` páry:  
  
```sql
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Chcete-li získat stejné výsledky pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], použijte odkaz na vlastnost `Orders` již existující ve třídě `Customer`. `Orders` odkaz poskytuje potřebné informace pro provedení dotazu a projektu `CustomerID`-`OrderID` páry, jako v následujícím kódu:  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Můžete také provést zpětný chod. To znamená, že se můžete dotazovat `Orders` a použít svůj odkaz na `Customer` vztah k informacím o přidruženém objektu `Customer`. Následující kód je stejný `CustomerID`-`OrderID` páry jako předtím, ale tentokrát pomocí dotazování `Orders` namísto `Customers`.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](query-concepts.md)
