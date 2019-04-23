---
title: 'Postupy: Mapování databázových relací'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 40e376f2c2584490273ec27b78fe5315cbb0315e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152877"
---
# <a name="how-to-map-database-relationships"></a>Postupy: Mapování databázových relací
Můžete kódovat jako vlastnost odkazuje ve své třídě entity žádné relace mezi daty, které budou vždy stejné. V ukázkové databázi Northwind třeba protože zákazníkům obvykle zadávat objednávky, není vždy relace v modelu mezi zákazníky a jejich objednávky.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definuje <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut nápovědy, představují tyto vztahy. Tento atribut se používá spolu s <xref:System.Data.Linq.EntitySet%601> a <xref:System.Data.Linq.EntityRef%601> typů k vyjádření, co by se vztahu cizího klíče v databázi. Další informace najdete v části atribut přidružení v [založených na atributech mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
> [!NOTE]
>  Hodnoty vlastností AssociationAttribute a ColumnAttribute úložiště jsou malá a velká písmena. Například Ujistěte se, že hodnoty atributu pro vlastnost AssociationAttribute.Storage rozlišovat velikost písmen pro odpovídající názvy vlastností používá jinde v kódu. To platí pro všechny programovací jazyky .NET, včetně těch, které nejsou obvykle velká a malá písmena, včetně jazyka Visual Basic. Další informace o vlastnosti úložiště najdete v tématu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 Většina relací jsou 1 n, stejně jako v příkladu dále v tomto tématu. Relace 1: 1 a many-to-many může také představovat následujícím způsobem:  
  
-   1: 1: Tento typ relace představují zahrnutím <xref:System.Data.Linq.EntitySet%601> na obou stranách.  
  
     Představte si třeba `Customer` - `SecurityCode` relace vytvořená tak, aby zákazníka bezpečnostní kód nebude nalezena instančním `Customer` tabulky a je přístupný jenom autorizované osoby.  
  
-   Many-to-many: Ve vztazích many-to-many, primární klíč tabulky odkaz (také s názvem *spojení* tabulky) je často vytvořené metodou složeného cizích klíčů z dalších dvou tabulek.  
  
     Představte si třeba `Employee` - `Project` many-to-many relace vytvořená s použitím vazební tabulka `EmployeeProject`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vyžaduje, aby takové relace modelovat pomocí tří tříd: `Employee`, `Project`, a `EmployeeProject`. V tomto případě změny vztahů mezi `Employee` a `Project` můžete zobrazit tak, aby vyžadovala aktualizace primárního klíče `EmployeeProject`. Ale je tato situace nejlépe modelovaná jako odstranění existující `EmployeeProject` a vytvoření nového `EmployeeProject`.  
  
    > [!NOTE]
    >  Relace v relačních databázích jsou obvykle nemodelují jako hodnoty cizího klíče, které odkazují na primárních klíčů v jiných tabulkách. K navigaci mezi nimi explicitně přidružíte dvě tabulky s využitím relační *spojení* operace.  
    >   
    >  Objekty v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], na druhé straně, odkazovat na sebe navzájem pomocí odkazy na vlastnosti nebo kolekce odkazů, které můžete procházet pomocí *tečkou* zápis.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu 1 n `Customer` třída obsahuje vlastnosti, která deklaruje vztah mezi zákazníky a jejich objednávky.  `Orders` Vlastnost je typu <xref:System.Data.Linq.EntitySet%601>. Tento typ označuje, že je tento vztah jeden mnoho (jednoho zákazníka na velké množství objednávek). <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> Vlastnost se používá k popisu, jak se provádí toto přidružení, konkrétně tak, že zadáte název vlastnosti ve třídě související k porovnání s touto verzí. V tomto příkladu `CustomerID` se porovnává vlastnost, stejně jako databázi *spojení* by porovnání hodnotě sloupce.  
  
> [!NOTE]
>  Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vytvoření přidružení mezi třídami.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Lze také zrušit situace. Namísto použití `Customer` tříd k popisu přidružení mezi zákazníci a objednávky, můžete použít `Order` třídy. `Order` Třídy používá <xref:System.Data.Linq.EntityRef%601> typu, který popisuje relace zpět na zákazníka, jako v následujícím příkladu kódu.  
  
> [!NOTE]
>  <xref:System.Data.Linq.EntityRef%601> Třídy podporuje *odložené načítání*. Další informace najdete *naleznete v tématu* [odložené versus okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
