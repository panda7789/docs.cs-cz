---
title: 'Postupy: vytvoření dynamicky databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: 122eb705838da00fedd77a01a5d8c4bd3b5f774e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-dynamically-create-a-database"></a>Postupy: vytvoření dynamicky databáze
V technologii LINQ to SQL objektový model je namapována na relační databázi. Mapování je povolený pomocí mapování na základě atributů nebo soubor externí mapování k popisu struktury relační databáze. V obou případech je dostatek informací o relační databázi, můžete vytvořit novou instanci databáze pomocí <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda.  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda vytváří repliku databáze rozsah informace kódovaný v objektovém modelu. Mapování soubory a atributy z modelu objektu nemusí zakódovat všechno, co o struktuře existující databázi. Informace o mapování nemá představují obsah uživatelsky definované funkce, uložené procedury, triggery, nebo omezení check. Toto chování je dostatečné pro různé databáze.  
  
 Můžete použít <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda v libovolný počet scénářů, hlavně pokud zprostředkovatele dat známé jako je Microsoft SQL Server 2008 je k dispozici. Typické scénáře patří:  
  
-   Vytváříte aplikaci, která automaticky nainstaluje systému zákazníka.  
  
-   Vytváříte klientská aplikace vyžadující místní databáze pro uložení stavu offline.  
  
 Můžete také <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metoda s SQL serverem pomocí souboru .mdf nebo název katalogu, v závislosti na připojovací řetězec. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] používá připojovací řetězec k definování databáze, který se má vytvořit a na serveru, který má být vytvořen databáze.  
  
> [!NOTE]
>  Kdykoli je to možné, použijte integrované zabezpečení systému Windows pro připojení k databázi tak, aby hesla nejsou potřebné v připojovacím řetězci.  
  
## <a name="example"></a>Příklad  
 Následující kód představuje příklad, jak vytvořit novou databázi s názvem MyDVDs.mdf.  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a>Příklad  
 K vytvoření databáze pomocí následujícího postupu můžete v objektovém modelu:  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Při vytváření aplikace, který automaticky nainstaluje sám systému zákazníka, najdete v části Pokud databázi již existuje a umístěte jej před vytvořením nového. <xref:System.Data.Linq.DataContext> Třída poskytuje <xref:System.Data.Linq.DataContext.DatabaseExists%2A> a <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> metody, které vám pomohou s tímto procesem.  
  
 Následující příklad ukazuje jeden ze způsobů, které tyto metody lze použít k implementaci tohoto přístupu:  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Viz také  
 [Mapování na základě atributů](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [Externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
