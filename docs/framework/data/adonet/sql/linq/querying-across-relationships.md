---
title: Dotazování napříč relacemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: be0aea66f0923b8b353f42cecc9360731efc7bb9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792844"
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
  
 Z toho vyplývá, že vlastnosti vztahu jsou důležitější než na straně výsledků dotazu, než jako součást dotazu samotného. Poté, co dotaz načte data o konkrétním zákazníkovi, definice třídy označuje, že zákazníci mají objednávky. Jinými slovy, očekáváte `Orders` , že vlastnost určitého zákazníka bude kolekce, která je vyplněna všemi objednávkami tohoto zákazníka. To je ve skutečnosti kontrakt, který jste deklarovali definováním tříd tímto způsobem. Očekává se, že se zobrazí objednávky i v případě, že dotaz nepožadoval objednávky. Očekáváte, že objektový model udržuje iluzi, že se jedná o příponu v paměti databáze se souvisejícími objekty hned dostupnými.  
  
 Teď, když máte relace, můžete napsat dotazy odkazem na vlastnosti vztahu definované ve vašich třídách. Tyto odkazy na relace odpovídají vztahům cizího klíče v databázi. Operace, které tyto relace používají, se převádějí do složitějších spojení v ekvivalentním kódu SQL. Pokud jste definovali relaci (pomocí <xref:System.Data.Linq.Mapping.AssociationAttribute> atributu), nemusíte kód explicitní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]spojení nakódovat.  
  
 Pro usnadnění zachování tohoto iluze [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje techniku s názvem *odložené načítání*. Další informace najdete v tématu [odložené porovnání a okamžité načítání](deferred-versus-immediate-loading.md).  
  
 Vezměte v úvahu následující dotaz SQL pro projektování seznamu `CustomerID` - `OrderID` párů:  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Chcete-li získat stejné výsledky pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], použijte `Customer` odkaz na `Orders` vlastnost již existující ve třídě. Odkaz poskytuje potřebné informace pro spuštění dotazu - a `OrderID` `CustomerID` projekt párů, jak je uvedeno v následujícím kódu: `Orders`  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Můžete také provést zpětný chod. To znamená, že se můžete `Orders` dotazovat a `Customer` použít svůj odkaz na relaci pro přístup k `Customer` informacím o přidruženém objektu. Následující kód projektuje `CustomerID` stejné - `OrderID` páry jako `Orders` předtím, `Customers`ale tentokrát se dotazuje namísto.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](query-concepts.md)
