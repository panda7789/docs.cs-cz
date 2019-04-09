---
title: 'Postupy: Přímé spuštění dotazů SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 6423959ed5036cc8ab2a88bb7273ef7aa95c8958
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101533"
---
# <a name="how-to-directly-execute-sql-queries"></a>Postupy: Přímé spuštění dotazů SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá dotazy, který napíšete do parametrizované dotazy jazyka SQL (ve formě textu) a odesílá je do serveru SQL server pro zpracování.  
  
 SQL nelze provést různými metodami, které mohou být místně dostupný vaší aplikaci. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se pokusí převést tyto místní metody na ekvivalentní operacemi a funkcemi, které jsou k dispozici v prostředí SQL. Většina metod a operátory na [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] vestavěné typy mají přímé překlady příkazy jazyka SQL. Některé je možné vytvořit z funkcí, které jsou k dispozici. Ty, které není možné generovat výjimky za běhu. Další informace najdete v tématu [mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 V případech, kde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu není dostatečná pro specializované úlohy, můžete použít <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> má metoda spustí dotaz SQL a poté převést výsledek dotazu přímo do objektů.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se předpokládá, že data `Customer` třídy se pak rozdělí více než dvě tabulky (customer1 a customer2). Dotaz vrátí sekvenci `Customer` objekty.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Za předpokladu, názvy sloupců v tabulkové výsledky odpovídají sloupec vlastnosti vaší entity třídy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvoří objekty mimo jakýkoli dotaz SQL.  
  
## <a name="example"></a>Příklad  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda také umožňuje pro parametry. Použijte například následující kód k provedení parametrický dotaz.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 Parametry jsou vyjádřeny v textu dotazu pomocí stejné složených zápisu používají `Console.WriteLine()` a `String.Format()`. Ve skutečnosti `String.Format()` ve skutečnosti je volán na řetězec dotazu, který zadáte, nahraďte složených závorkách parametry s generované názvy parametrů, jako @p0, @p1 ..., @p(n).  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Dotazy do databáze](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
