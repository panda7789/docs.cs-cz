---
title: "Určit, zda některé nebo všechny elementy v pořadí nesplňuje podmínku"
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
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 29b9b79915e94ed1015c7869692647c10da58f60
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Určit, zda některé nebo všechny elementy v pořadí nesplňuje podmínku
<xref:System.Linq.Enumerable.All%2A> Vrátí operátor `true` Pokud všechny elementy v pořadí splňují podmínku.  
  
 <xref:System.Linq.Queryable.Any%2A> Vrátí operátor `true` Pokud libovolný prvek v pořadí splňuje podmínku.  
  
## <a name="example"></a>Příklad  
 Následující příklad vrací posloupnost zákazníků, kteří mají alespoň jednu objednávku. `Where` / `where` Klauzule se vyhodnocuje `true` Pokud v dané `Customer` obsahuje některý `Order`.  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Příklad  
 Následující kód jazyka Visual Basic určuje seznamu zákazníků, kteří nejsou umístěny objednávky a zajišťuje, že pro každý zákazník v tomto seznamu, jméno kontaktní osoby je k dispozici.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Příklad  
 Následující příklad jazyka C# vrací posloupnost zákazníků, jejichž objednávky mají `ShipCity` počínaje "C". Také součástí návratový jsou zákazníci, kteří nemají žádnou objednávku. (Standardně <xref:System.Linq.Queryable.All%2A> vrátí operátor `true` pro prázdnou sekvencí.) Zákazníci bez objednávek se eliminovala ve výstupu konzoly pomocí `Count` operátor.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Viz také  
 [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
