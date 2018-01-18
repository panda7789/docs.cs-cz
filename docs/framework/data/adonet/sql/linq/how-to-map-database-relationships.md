---
title: "Postupy: mapování relace databáze"
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
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b1637fd322468f743c29605b31c3c6849bd78aa6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-map-database-relationships"></a>Postupy: mapování relace databáze
Můžete zakódovat jako odkazuje vlastnost v třídě entity žádné vztahy dat, které budou vždy stejné. Ukázková databáze Northwind například vzhledem k tomu, že zákazníci obvykle umístit objednávky, je vždy vztah v modelu mezi zákazníků a jejich objednávky.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]definuje <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut pomohou představují takové vztahy. Tento atribut slouží společně s <xref:System.Data.Linq.EntitySet%601> a <xref:System.Data.Linq.EntityRef%601> typy představují, co by relace cizího klíče v databázi. Další informace najdete v tématu části přidružení atribut [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
> [!NOTE]
>  Hodnoty vlastností AssociationAttribute a ColumnAttribute úložiště rozlišují malá a velká písmena. Například zajistěte, že hodnoty atributu pro vlastnost AssociationAttribute.Storage malá a velká písmena pro odpovídající vlastnost názvy používá někde v kódu. To platí pro všechny programovacích jazyků .NET, včetně těch, které nejsou obvykle velká a malá písmena, včetně [!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)]. Další informace o vlastnosti úložiště najdete v tématu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 Jeden mnoho, jako v příkladu dále v tomto tématu se většina vztahy. Můžete také představovat relace 1: 1 a m: n následujícím způsobem:  
  
-   1: 1: Tento typ vztahu představují zahrnutím <xref:System.Data.Linq.EntitySet%601> na obou stranách.  
  
     Představte si třeba `Customer` - `SecurityCode` relace vytvořená tak, aby zákazníka bezpečnostní kód nebude nalezeno v `Customer` tabulky a lze k němu přístup pouze oprávněných osob.  
  
-   M m: V relace m: n, primární klíč tabulky odkaz (také s názvem *spojení* tabulky) je často formátu složeného cizího klíče z obou tabulek.  
  
     Představte si třeba `Employee` - `Project` relace m: n vytvořená pomocí tabulky odkaz `EmployeeProject`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]vyžaduje, aby takové relace modelovat pomocí tří tříd: `Employee`, `Project`, a `EmployeeProject`. V takovém případě změna vztah mezi `Employee` a `Project` můžete zobrazit tak, aby vyžadovala aktualizace primární klíč `EmployeeProject`. Však tato situace je nejlépe modelován jako odstranění existující `EmployeeProject` a vytvoření nové `EmployeeProject`.  
  
    > [!NOTE]
    >  Vztahy v relačních databází jsou obvykle modelován jako hodnoty cizího klíče, které odkazují na primárních klíčů v jiné tabulky. Umožňují přecházet mezi jednotlivými je explicitně přidružíte dvě tabulky pomocí relační *spojení* operaci.  
    >   
    >  Objekty v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], na dalším ruční, odkazovat navzájem pomocí vlastnosti odkazy nebo kolekce odkazy, které přejdete pomocí *tečkou* zápis.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jeden mnoho `Customer` třída obsahuje vlastnosti, který deklaruje vztah mezi zákazníků a jejich objednávky.  `Orders` Vlastnost je typu <xref:System.Data.Linq.EntitySet%601>. Tento typ označuje, že je tento vztah jeden mnoho (jedno zákazníka na mnoho objednávky). <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> Vlastnost se používá k popisu, jak toto přidružení se provádí, konkrétně, tak, že zadáte název vlastnosti v související třídy, který se má porovnat s Tato. V tomto příkladu `CustomerID` vlastnost porovnání, stejně jako databázi *spojení* by porovnat hodnotě sloupce.  
  
> [!NOTE]
>  Pokud používáte [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vytvoření přidružení mezi třídami.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Můžete také nechat provést zpětnou situaci. Místo použití `Customer` třídy k popisu přidružení mezi zákazníci a objednávky, můžete použít `Order` třídy. `Order` Třídy používá <xref:System.Data.Linq.EntityRef%601> typu, který popisuje relace zpět k zákazníka, jako v následujícím příkladu kódu.  
  
> [!NOTE]
>  <xref:System.Data.Linq.EntityRef%601> Třídy podporuje *odložené načítání*. Další informace najdete *najdete v části* [odložení versus okamžitou načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
