---
title: 'Postupy: Dynamické vytvoření databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: e5d66b49782d5f26b6d487e655aca6fbd6bdfb1a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623866"
---
# <a name="how-to-dynamically-create-a-database"></a>Postupy: Dynamické vytvoření databáze
V technologii LINQ to SQL objektový model je namapována na relační databáze. Mapování je povolit pomocí podle atributů mapování nebo souboru externí mapování k popisu struktury relační databáze. V obou případech je dostatek informací o relační databázi, můžete vytvořit novou instanci používat databázi <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody.  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda vytvoří replika databáze rozsah informace kódovaný v objektovém modelu. Mapování souborů a atributy z objektového modelu nemusí kódování všechno o struktuře existující databázi. Informace o mapování neobsahuje představují obsah uživatelsky definovaných funkcí, uložené procedury, triggery, nebo kontrola omezení. Toto chování je dostatečná pro širokou škálu databází.  
  
 Můžete použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda v jakémkoli počtu scénářů, zejména v případě, že zprostředkovatel známé dat, jako je Microsoft SQL Server 2008 je k dispozici. Typické scénáře zahrnují následující:  
  
- Vytváříte aplikaci, která se automaticky nainstaluje na systému zákazníky.  
  
- Sestavujete klientské aplikace, která potřebuje místní databáze pro uložení stavu offline.  
  
 Můžete také použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda s SQL serverem pomocí souboru .mdf nebo název katalogu, v závislosti na tom, aby váš připojovací řetězec. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] použití připojovacího řetězce k definování databáze, kterou chcete vytvořit, a na serveru, který se má vytvořit databázi.  
  
> [!NOTE]
>  Kdykoli je to možné, použijte integrované zabezpečení Windows pro připojení k databázi tak, aby hesla nejsou vyžadovány v připojovacím řetězci.  
  
## <a name="example"></a>Příklad  
 Následující kód obsahuje příklad toho, jak vytvořit novou databázi s názvem MyDVDs.mdf.  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a>Příklad  
 Objektový model můžete použít k vytvoření databáze následujícím způsobem:  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Při vytváření aplikace, které automaticky nainstaluje sám systému zákazníků, najdete v článku Pokud databáze již existuje a umístěte jej před vytvořením nového. <xref:System.Data.Linq.DataContext> Třída poskytuje <xref:System.Data.Linq.DataContext.DatabaseExists%2A> a <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> metody, které vám pomůžou se tento proces.  
  
 Následující příklad ukazuje jeden způsob, jakým tyto metody slouží k implementaci tohoto přístupu:  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- [Mapování na základě atributů](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [Mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
