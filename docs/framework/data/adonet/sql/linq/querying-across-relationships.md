---
title: "Dotazování napříč relacemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f06297f79807a1548a6b5ac77aed45f52c8d03af
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="querying-across-relationships"></a>Dotazování napříč relacemi
Odkazy na jiné objekty nebo kolekce jiných objektů ve vaší definice tříd přímo odpovídají relace cizího klíče v databázi. Tyto relace můžete použít při dotazování podle pomocí zápisu s tečkou přístup k vlastnosti vztahu a přejít z jednoho objektu na jiný. Tyto operace přístupu převede složitější spojení nebo korelační poddotazy v ekvivalentní SQL.  
  
 Například následující dotaz přejde z objednávek zákazníků jako způsob, jak omezit výsledky pouze příkazy pro zákazníky, které jsou umístěny v Londýně.  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 Vlastnosti vztahu neexistovala bude potřeba je napsat ručně jako *spojení*, stejně, jako byste to udělali v dotazu SQL, jako v následujícím kódu:  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 Můžete použít *vztah* vlastnost k definování této konkrétní relace jednou. Potom můžete pohodlnější tečkové syntaxe. Ale vlastnosti vztahu existovat je důležité, protože specifické pro doménu objektové modely jsou obvykle definovány jako hierarchie nebo grafy. Objekty, které plánujete mít odkazy na jiné objekty. Je pouze radostí shoda, která odpovídají objekt objektu relace cizího klíče ve vztahy v databázích. Přístup k vlastnosti pak představuje pohodlný způsob pro zápis spojení.  
  
 S ohledem na to jsou důležitější na straně výsledků dotazu než jako součást dotazu, samotné vlastnosti vztahu. Po dotazu byla načtena data o konkrétního zákazníka, definice třídy znamená, že zákazníci mají objednávky. Jinými slovy, byste měli `Orders` vlastnost konkrétního zákazníka jako kolekce, která se zobrazí v všechny objednávky z tohoto zákazníka. To je ve skutečnosti smlouvu, kterou deklarovaná definice tříd tímto způsobem. Byste měli vidět objednávky existuje i v případě, že dotaz nepožádali objednávky. Očekáváte objekt modelu k udržování dojem, že je v paměti rozšíření databáze s souvisejících objektů, které okamžitě k dispozici.  
  
 Teď, když máte relace, můžete psát dotazy tím, že odkazuje na relaci vlastnosti definované v tříd. Tyto odkazy vztah odpovídají relace cizího klíče v databázi. Operace, které používají tyto vztahy se převede do složitější spojení v ekvivalentní SQL. Tak dlouho, dokud jste definovali vztahu (pomocí <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut), nemusíte kód explicitní spojení v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Které pomáhají udržovat tento iluzi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje techniku zvanou *odložené načítání*. Další informace najdete v tématu [odložení versus okamžitou načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 Vezměte v úvahu následující dotaz SQL, do projektu seznam `CustomerID` - `OrderID` páry:  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Získat stejné výsledky pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], můžete použít `Orders` vlastnost odkazovat, již existuje v `Customer` třídy. `Orders` Odkaz poskytuje informace potřebné k provedení dotazu a projekt `CustomerID` - `OrderID` páry, jako v následujícím kódu:  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Můžete také provést naopak. To znamená, že se můžete dotazovat `Orders` a použít jeho `Customer` vztah odkaz na přístup k informacím o přidruženého `Customer` objektu. Následující kód projekty stejné `CustomerID` - `OrderID` páry jako předtím, ale tentokrát dotazováním `Orders` místo `Customers`.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Viz také  
 [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
