---
title: 'Postupy: Dynamické vytvoření databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: 4cadf20cdadb39483f26a29619cae058eac47e50
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793660"
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

- [Mapování na základě atributů](attribute-based-mapping.md)
- [Externí mapování](external-mapping.md)
- [Mapování typů SQL a CLR](sql-clr-type-mapping.md)
- [Základní informace](background-information.md)
- [Vytvoření a odeslání změn dat](making-and-submitting-data-changes.md)
