---
title: Zřetězení dvou sekvencí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: b802abae9fc2c1731a623209862f61ed5ee51f9c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247889"
---
# <a name="concatenate-two-sequences"></a>Zřetězení dvou sekvencí
<xref:System.Linq.Queryable.Concat%2A> Použijte operátor ke zřetězení dvou sekvencí.  
  
 <xref:System.Linq.Queryable.Concat%2A> Operátor je definován pro seřazené množiny, kde jsou objednávky příjemce a argumentu stejné.  
  
 Řazení v SQL je posledním krokem před tím, než se vytvoří výsledky. Z <xref:System.Linq.Queryable.Concat%2A> tohoto důvodu je operátor implementován pomocí `UNION ALL` a nezachovává pořadí jeho argumentů. Chcete-li se ujistit, že je řazení ve výsledcích správné, ujistěte se, že jsou výsledky explicitně seřazeny.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> k vrácení posloupnosti `Employee` všech `Customer` telefonních a faxových čísel.  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Concat%2A> k vrácení posloupnosti mapování všech `Customer` názvů `Employee` a názvu a telefonního čísla.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](query-examples.md)
- [Převod standardních operátorů dotazů](standard-query-operator-translation.md)
