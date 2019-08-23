---
title: 'Postupy: Mapování databázových relací'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 42e7a715c8137574bff617715c1f174314080131
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943616"
---
# <a name="how-to-map-database-relationships"></a>Postupy: Mapování databázových relací
V rámci třídy entity můžete kódovat jako odkazy na vlastnosti všechny relace dat, které budou vždy stejné. Například vzhledem k tomu, že zákazníci obvykle umísťují objednávky, je v ukázkové databázi Northwind vždy relace v modelu mezi zákazníky a jejich objednávkami.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.AssociationAttribute> definuje atribut, který bude pomáhat tyto vztahy reprezentovat. Tento atribut se používá společně s <xref:System.Data.Linq.EntitySet%601> typy a <xref:System.Data.Linq.EntityRef%601> k reprezentaci toho, co by bylo relace cizího klíče v databázi. Další informace naleznete v části atributu přidružení v [mapování na základě atributů](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
> [!NOTE]
> Hodnoty vlastností úložiště AssociationAttribute a ColumnAttribute rozlišují velká a malá písmena. Například zajistěte, aby hodnoty použité v atributu vlastnosti AssociationAttribute. Storage odpovídaly velikosti písmen pro odpovídající názvy vlastností používané jinde v kódu. To platí pro všechny programovací jazyky rozhraní .NET, i ty, které se obvykle nerozlišují bez rozlišení velkých a malých písmen, včetně Visual Basic. Další informace o vlastnosti úložiště naleznete v tématu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 Většina relací je 1: n, jako v příkladu dále v tomto tématu. Můžete také znázornit relace 1:1 a m:n následujícím způsobem:  
  
- Jeden k jednomu: Představuje tento druh vztahu zahrnutím <xref:System.Data.Linq.EntitySet%601> na obě strany.  
  
     Předpokládejme `Customer` - například,že`Customer` je relace vytvořena tak, že kód zabezpečení zákazníka nebude v tabulce nalezen a bude k nim moci získat oprávnění pouze autorizovaní uživatelé. `SecurityCode`  
  
- Mnoho k mnoha: V relacích m:n je primární klíč tabulky odkazů (také označovaný jako *spojovací* tabulka) často tvořen složenými cizími klíči z dalších dvou tabulek.  
  
     Například je třeba vzít v `Employee` úvahu - `Project` vztah m:n vytvořený pomocí tabulky `EmployeeProject`propojit. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]vyžaduje, aby taková relace byla modelována pomocí tří tříd: `Employee`, `Project` `EmployeeProject`a. V takovém případě se `Employee` `Project` může zdát, že změna vztahu mezi a a bude pravděpodobně vyžadovat aktualizaci primárního klíče `EmployeeProject`. Tato situace je ale nejlépe namodelovaná jako odstranění existujícího `EmployeeProject` a vytvoření nového. `EmployeeProject`  
  
    > [!NOTE]
    > Relace v relačních databázích jsou obvykle modelované jako hodnoty cizích klíčů, které odkazují na primární klíče v jiných tabulkách. K procházení mezi nimi explicitně přiřadíte tyto dvě tabulky pomocí operace relačního *spojení* .  
    >   
    >  Objekty na druhé straně vzájemně odkazují pomocí odkazů na vlastnosti nebo kolekcí odkazů, které můžete procházet pomocí zápisu *teček.* [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Customer` má třída vlastnost, která deklaruje vztah mezi zákazníky a jejich objednávkami.  Vlastnost je typu <xref:System.Data.Linq.EntitySet%601>. `Orders` Tento typ znamená, že je tento vztah 1: n (jeden zákazník k mnoha objednávkám). <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> Vlastnost se používá k popisu způsobu, jakým je toto přidružení provedeno, konkrétně zadáním názvu vlastnosti v související třídě, která má být porovnána s touto. V tomto příkladu `CustomerID` je porovnávána vlastnost, stejně jako *spojení* databáze, porovnává tuto hodnotu sloupce.  
  
> [!NOTE]
> Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů k vytvoření přidružení mezi třídami.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Můžete také změnit situaci. Namísto použití `Customer` třídy pro popis přidružení mezi zákazníky a objednávkami, můžete `Order` použít třídu. `Order` Třída<xref:System.Data.Linq.EntityRef%601> používá typ k popisu vztahu zpět k zákazníkovi, jak je uvedeno v následujícím příkladu kódu.  
  
> [!NOTE]
> Třída podporuje *odložené načítání.* <xref:System.Data.Linq.EntityRef%601> Další informace *najdete v tématu* [odložené porovnání a okamžité načítání](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
