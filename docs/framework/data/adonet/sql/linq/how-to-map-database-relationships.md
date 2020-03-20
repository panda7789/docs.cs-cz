---
title: 'Postupy: Mapování databázových relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: c89fb3e11ae8e0f8ea37727446cdf65db9499a1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148371"
---
# <a name="how-to-map-database-relationships"></a>Postupy: Mapování databázových relace
Můžete kódovat jako odkazy na vlastnosti ve vaší třídě entity všechny datové vztahy, které budou vždy stejné. V ukázkové databázi Northwind, například protože zákazníci obvykle zadávat objednávky, je vždy vztah v modelu mezi zákazníky a jejich objednávky.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]definuje <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut, který pomáhá reprezentovat tyto vztahy. Tento atribut se používá <xref:System.Data.Linq.EntitySet%601> <xref:System.Data.Linq.EntityRef%601> společně s a typy představují co by byl vztah cizího klíče v databázi. Další informace naleznete v části Atribut přidružení [v mapování založeném na atributech](attribute-based-mapping.md).  
  
> [!NOTE]
> Hodnoty vlastností AssociationAttribute a ColumnAttribute Storage rozlišují malá a velká písmena. Například zajistěte, aby hodnoty použité v atributu vlastnosti AssociationAttribute.Storage odpovídaly případu odpovídajících názvů vlastností použitých jinde v kódu. To platí pro všechny programovací jazyky .NET, i ty, které nejsou obvykle malá a velká písmena, včetně jazyka Visual Basic. Další informace o vlastnosti <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>Storage naleznete v tématu .  
  
 Většina vztahů je 1:N, jako v příkladu dále v tomto tématu. Můžete také představovat relace 1:1 a N:N takto:  
  
- One-to-one: Představují tento druh <xref:System.Data.Linq.EntitySet%601> vztahu tím, že na obou stranách.  
  
     `Customer` - `SecurityCode` Zvažte například vztah vytvořený tak, aby bezpečnostní kód zákazníka `Customer` nebyl v tabulce nalezen a byl přístupný pouze oprávněným osobám.  
  
- N:N: V relacích N:N je primární klíč tabulky propojení (také pojmenovaný *spojovací* tabulka) často tvořen složenými cizími klíči z ostatních dvou tabulek.  
  
     Zvažte například `Employee` - `Project` relaci N:N vytvořenou pomocí `EmployeeProject`tabulky odkazů . [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]vyžaduje, aby byl takový vztah modelován `Project`pomocí `EmployeeProject`tří tříd: `Employee`, , a . V takovém případě může změna `Employee` vztahu `Project` mezi a a a vyžadovat `EmployeeProject`aktualizaci primárního klíče . Tato situace je však nejlépe modelován `EmployeeProject` jako odstranění `EmployeeProject`existující a vytvoření nového .  
  
    > [!NOTE]
    > Vztahy v relačních databázích jsou obvykle modelovány jako hodnoty cizího klíče, které odkazují na primární klíče v jiných tabulkách. Chcete-li procházet mezi nimi explicitně přidružit dvě tabulky pomocí operace relační *spojení.*  
    >
    >  Objekty [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]v , na druhé straně odkazují na sebe pomocí odkazy vlastností nebo kolekce odkazů, které procházíte pomocí *tečka* zápisu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu 1:N `Customer` má třída vlastnost, která deklaruje vztah mezi zákazníky a jejich objednávkami.  Vlastnost `Orders` je typu <xref:System.Data.Linq.EntitySet%601>. Tento typ znamená, že tento vztah je 1:N (jeden zákazník na mnoho objednávek). Vlastnost <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> se používá k popisu, jak je toto přidružení dosaženo, konkrétně zadáním názvu vlastnosti v související třídě, která má být porovnána s touto. V tomto příkladu `CustomerID` je porovnána vlastnost, stejně jako *spojení* databáze by porovnat tuto hodnotu sloupce.  
  
> [!NOTE]
> Pokud používáte Visual Studio, můžete použít objekt relační návrhář k vytvoření přidružení mezi třídami.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Můžete také zvrátit situaci. Namísto použití `Customer` třídy k popisu přidružení mezi zákazníky `Order` a objednávkami můžete třídu použít. Třída `Order` používá <xref:System.Data.Linq.EntityRef%601> typ k popisu vztahu zpět k zákazníkovi, jako v následujícím příkladu kódu.  
  
> [!NOTE]
> Třída <xref:System.Data.Linq.EntityRef%601> podporuje *odložené načítání*. Další informace naleznete v *tématu* [Odloženo versus okamžité načtení](deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také

- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
