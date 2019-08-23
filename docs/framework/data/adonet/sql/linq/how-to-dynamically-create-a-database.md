---
title: 'Postupy: Dynamické vytvoření databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: 92db9bdb209a542cc4fa269b35bfa98f8f20d2b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940077"
---
# <a name="how-to-dynamically-create-a-database"></a>Postupy: Dynamické vytvoření databáze
V LINQ to SQL objektový model je namapován na relační databázi. Mapování je povoleno pomocí mapování založeného na atributech nebo souboru externího mapování pro popis struktury relační databáze. V obou scénářích je k dispozici dostatek informací o relační databázi, kterou můžete vytvořit novou instanci databáze pomocí <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody.  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda vytvoří repliku databáze pouze v rozsahu informací zakódovaných v objektovém modelu. Mapování souborů a atributů z objektového modelu nemusí zakódovat vše o struktuře existující databáze. Informace o mapování nepředstavuje obsah uživatelsky definovaných funkcí, uložených procedur, triggerů nebo omezení CHECK. Toto chování je dostatečné pro nejrůznější databáze.  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metodu můžete použít v jakémkoli počtu scénářů, zejména pokud je k dispozici známý poskytovatel dat, jako je Microsoft SQL Server 2008. Mezi typické scénáře patří následující:  
  
- Vytváříte aplikaci, která se automaticky nainstaluje do zákaznického systému.  
  
- Vytváříte klientskou aplikaci, která potřebuje místní databázi pro uložení stavu offline.  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metodu můžete také použít s SQL Server pomocí souboru. MDF nebo názvu katalogu v závislosti na vašem připojovacím řetězci. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pomocí připojovacího řetězce definuje databázi, která se má vytvořit, a na kterých serveru se databáze má vytvořit.  
  
> [!NOTE]
> Kdykoli je to možné, použijte integrované zabezpečení systému Windows pro připojení k databázi, aby se v připojovacím řetězci nevyžadovala hesla.  
  
## <a name="example"></a>Příklad  
 Následující kód poskytuje příklad vytvoření nové databáze s názvem MyDVDs. mdf.  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a>Příklad  
 Objektový model můžete použít k vytvoření databáze pomocí následujícího postupu:  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Při sestavování aplikace, která se automaticky nainstaluje do systému zákazníka, si přečtěte téma, jestli databáze už existuje, a vyřaďte ji ještě předtím, než vytvoříte novou. Třída poskytuje metody<xref:System.Data.Linq.DataContext.DeleteDatabase%2A> a, které vám pomůžou s tímto procesem. <xref:System.Data.Linq.DataContext.DatabaseExists%2A> <xref:System.Data.Linq.DataContext>  
  
 Následující příklad ukazuje jeden ze způsobů, jak lze tyto metody použít k implementaci tohoto přístupu:  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- [Mapování na základě atributů](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [Mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
