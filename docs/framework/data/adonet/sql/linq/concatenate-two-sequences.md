---
title: Zřetězení dvou sekvencí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: 831905ca5a712bcb80d5bab1aef61a81d2ade1b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734272"
---
# <a name="concatenate-two-sequences"></a>Zřetězení dvou sekvencí
Použití <xref:System.Linq.Queryable.Concat%2A> operátoru pro zřetězení dvou sekvencí.  
  
 <xref:System.Linq.Queryable.Concat%2A> Operátor je definován pro uspořádaný multisets kde objednávky příjemce a argument jsou stejné.  
  
 Řazení v SQL je posledním krokem předtím, než se produkují výsledky. Z tohoto důvodu <xref:System.Linq.Queryable.Concat%2A> operátor je implementovaný s využitím `UNION ALL` a nezachovávat hodnotu pořadí z jejích argumentů. Ujistěte se, že pořadí je správné výsledky, ujistěte se, že explicitně řazení výsledků.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> k vrácení sekvence všech `Customer` a `Employee` číslo telefonu a faxu.  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> k vrácení sekvence všech `Customer` a `Employee` pojmenujte a telefonní číslo mapování.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>Viz také:
- [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Převod standardních operátorů dotazů](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
