---
title: 'Postupy: Přímé spuštění dotazů SQL'
description: Naučte se používat ExecuteQuery ke spuštění dotazu a následnému převedení výsledků přímo do objektů v případech, kdy je LINQ to SQL dotaz nedostatečný.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 59bd404e41f6be1181d6a625c31ee23358db0df3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286362"
---
# <a name="how-to-directly-execute-sql-queries"></a>Postupy: Přímé spuštění dotazů SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]přeloží dotazy zapsané do parametrizovaných dotazů SQL (v textovém formátu) a pošle je do SQL serveru pro zpracování.  
  
 SQL nemůže spustit celou řadu metod, které mohou být k dispozici místně pro vaši aplikaci. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pokusí se převést tyto místní metody na ekvivalentní operace a funkce, které jsou k dispozici v prostředí SQL. Většina metod a operátorů v .NET Framework předdefinovaných typů má přímé překlady do příkazů SQL. Některé mohou být vytvořeny z dostupných funkcí. Ty, které se nedají vyrobit, generují výjimky za běhu. Další informace naleznete v tématu [mapování typu SQL-CLR](sql-clr-type-mapping.md).  
  
 V případech, kdy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] je dotaz nedostatečný pro specializovanou úlohu, lze použít <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metodu pro spuštění dotazu SQL a následně převést výsledek dotazu přímo do objektů.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu Předpokládejme, že data pro `Customer` třídu jsou rozložena do dvou tabulek (Customer1 a Customer2). Dotaz vrátí sekvenci `Customer` objektů.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Pokud názvy sloupců v tabulkových výsledcích odpovídají vlastnostem sloupce vaší třídy entity, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří objekty mimo libovolný dotaz SQL.  
  
## <a name="example"></a>Příklad  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A>Metoda také umožňuje parametry. Použijte následující kód k provedení parametrizovaného dotazu.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 Parametry jsou vyjádřeny v textu dotazu pomocí stejného složeného zápisu, který používá `Console.WriteLine()` a `String.Format()` . Ve skutečnosti `String.Format()` je ve skutečnosti volána v řetězci dotazu, který zadáte, a nahrazením složených složených parametrů názvy generovaných parametrů, jako například @p0 , @p1 ..., @p (n).  
  
## <a name="see-also"></a>Viz také

- [Základní informace](background-information.md)
- [Dotazování na databázi](querying-the-database.md)
