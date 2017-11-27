---
title: "Příklady dotazů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e7d7a0a1f641603887675ed0c1faebd5c06b273
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="query-examples"></a>Příklady dotazů
Tato část obsahuje [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] a C# Příklady typických [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy. Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] najdete mnoho další příklady v ukázkové řešení, která je k dispozici v části Ukázky. Další informace najdete v tématu [ukázky](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).  
  
> [!IMPORTANT]
>  *DB* se často používá v příklady kódu v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dokumentaci. *DB* se považuje za instanci *Northwind* třídy, která dědí z <xref:System.Data.Linq.DataContext>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Agregační dotazy](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 Popisuje způsob použití <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, a tak dále.  
  
 [Vrátí první prvek v pořadí](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.First%2A>.  
  
 [Vrátí nebo přeskočit elementy v pořadí](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A>.  
  
 [Řazení elementů v pořadí](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.OrderBy%2A>.  
  
 [Prvky skupiny v pořadí](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.GroupBy%2A>.  
  
 [Odstranit elementy s duplicitním z řady](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.Distinct%2A>.  
  
 [Určit, zda některé nebo všechny elementy v pořadí nesplňuje podmínku](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.All%2A> a <xref:System.Linq.Enumerable.Any%2A>.  
  
 [Řetězení dvě pořadí](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.Concat%2A>.  
  
 [Vrátí množinových rozdílů mezi dvěma pořadí](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.Except%2A>.  
  
 [Vrátí sadu průnik dvou sekvencí](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.Intersect%2A>.  
  
 [Vrátí sadu sjednocení dvou sekvencí](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.Union%2A>.  
  
 [Převod na pole sekvenci](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.ToArray%2A>.  
  
 [Převést na seznam obecná posloupnost](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.ToList%2A>.  
  
 [Převést typ na obecný IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 Obsahuje příklady použití <xref:System.Linq.Enumerable.AsEnumerable%2A>.  
  
 [Formulovali spojení a dotazy smíšený produkt](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 Obsahuje příklady použití navigační cizího klíče v `from`, `where`, a `select` klauzule.  
  
 [Formulovali projekce](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 Obsahuje příklady kombinování `select` s jinými funkcemi (například *anonymní typy*) do formuláře dotazu projekce.  
  
## <a name="related-sections"></a>Související oddíly  
 [Přehled standardních operátorů dotazu](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 Popisuje koncept standardní operátory dotazu.  
  
 [Koncepty dotazu](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 Vysvětluje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používá koncepty, které platí pro dotazy.  
  
 [Průvodce programováním](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 Poskytuje portál na témata, které vysvětlují, související s koncepty programování [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].
