---
title: Dotazování napříč relacemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: 2e1cf9efcf47fc70421c64541aead5fb36d8c9d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916770"
---
# <a name="querying-across-relationships"></a>Dotazování napříč relacemi
Odkazy na jiné objekty nebo kolekce jiných objektů ve svých definicích třídy přímo odpovídají vztahy cizího klíče v databázi. Tyto vztahy můžete použít při dotazování pomocí zápisu s tečkou pro přístup k vlastnosti relace a přejít z jednoho objektu na jiný. Tyto operace přístupu přeložit více komplexním spojením nebo korelační poddotazy v ekvivalentní SQL.  
  
 Například následující dotaz přejde z objednávek zákazníků jako způsob, jak omezit výsledky pouze příkazy pro zákazníci, kteří žijí v Londýně.  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 Pokud neexistuje vlastnosti vztahu potřeba je napsat ručně jako *spojení*stejně, jako byste to udělali v dotazu SQL, stejně jako v následujícím kódu:  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 Můžete použít *vztah* vlastnost pro definování této konkrétní relaci jednou. Potom můžete pohodlnější tečkové syntaxe. Ale vlastnosti vztahu existovat ještě důležitější, protože objekt doménově specifické modely jsou obvykle definovány jako hierarchie nebo grafy. Objekty, které můžete programovat proti odkazují na jiné objekty. Je pouze odpovídající objektu do objektu relace cizího klíče styl vztahy v databázích všechno nejlepší shoda. Přístup k vlastnostem poskytuje pohodlný způsob, jak napsat spojení.  
  
 S ohledem na to jsou vlastnosti relace důležitějším na straně výsledků dotazu než jako součást samotný dotaz. Po dotaz načte data o určitého zákazníka, definice třídy označuje, že zákazníci mají objednávky. Jinými slovy, můžete očekávat `Orders` vlastnost určitého zákazníka kolekce, který je naplněn všech objednávek tohoto zákazníka. To je ve skutečnosti smlouvu, kterou jste deklarovali definováním třídy tímto způsobem. Byste měli vidět objednávky existuje i v případě, že dotaz nezažádali objednávky. Očekáváte, že váš model objektu udržovat dojem, že se jedná o rozšíření v paměti z databáze se souvisejícími objekty, které jsou okamžitě dostupné.  
  
 Teď, když máte relace, můžete psát dotazy rekapitulací vztah vlastnosti definované ve třídách. Tyto relace odkazy odpovídají vztahy cizího klíče v databázi. Operace, které používají tyto vztahy přeložit na složitější spojení v ekvivalentní SQL. Tak dlouho, dokud relace byla definována (pomocí <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut), nemají explicitní spojení v kódu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Zachovat tento dojem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje techniky označované jako *odložené načítání*. Další informace najdete v tématu [odložené versus okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 Vezměte v úvahu následující dotaz SQL, projektů seznam `CustomerID` - `OrderID` dvojice:  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Získání stejných výsledků pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], je použít `Orders` vlastnost odkazovat již existuje ve `Customer` třídy. `Orders` Informace potřebné k provedení dotazu a projekt obsahuje odkaz `CustomerID` - `OrderID` dvojice, stejně jako v následujícím kódu:  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Můžete také provést opačně. To znamená, můžete dát dotaz na `Orders` a použít jeho `Customer` vztah odkazu na přístup k informacím o přidruženého `Customer` objektu. Následující kód projekty stejné `CustomerID` - `OrderID` dvojice stejně jako předtím, ale tentokrát dotazováním `Orders` místo `Customers`.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
