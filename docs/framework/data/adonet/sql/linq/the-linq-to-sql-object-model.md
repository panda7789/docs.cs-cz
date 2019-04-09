---
title: Objektový model LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: 7ce759de004d479f5162d2ce3a965f5c40afa450
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110790"
---
# <a name="the-linq-to-sql-object-model"></a>Objektový model LINQ to SQL
V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], objektový model vyjádřený v programovacím jazyce vývojáře je namapována na datový model relační databáze. Operace s daty jsou pak provedeny podle modelu objektu.  
  
 V tomto scénáři není vydávat příkazy databáze (například `INSERT`) do databáze. Místo toho změnit hodnoty a spouštět metody v rámci objektu modelu. Pokud chcete zadat dotaz na databázi nebo odeslat změní, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] převádí vašich požadavků na správné příkazy SQL a odesílá tyto příkazy do databáze.  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Většina základních prvků v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model a jejich vztah k prvkům v relačním datovým modelem jsou shrnuty v následující tabulce:  
  
|Technologie LINQ to SQL objektový Model|Relační Data modelu|  
|------------------------------|---------------------------|  
|Třída entity|Tabulka|  
|Člen třídy|Sloupec|  
|Přidružení|Cizí klíč relace|  
|Metoda|Uložená procedura nebo funkce|  
  
> [!NOTE]
>  V následujících popisech Předpokládejme, že máte základní znalosti o relačním datovým modelem a pravidla.  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>Technologie LINQ to SQL tříd entit a tabulek databáze  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], je reprezentována tabulku databáze *třída entity*. Třídu entity je stejná jako jiné třídy, které můžete vytvořit s tím rozdílem, že přidání poznámek ke třídě pomocí speciální informace, které třídy přidruží databázové tabulky. Tato poznámka provedete tak, že přidáte vlastní atribut (<xref:System.Data.Linq.Mapping.TableAttribute>) k deklaraci vaší třídy, jako v následujícím příkladu:  
  
### <a name="example"></a>Příklad  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 Pouze instance třídy deklarované jako tabulky (to znamená, tříd entit) je možné ukládat do databáze.  
  
 Další informace najdete v části atribut tabulky v [založených na atributech mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>Technologie LINQ to SQL členy třídy a sloupce databáze  
 Kromě tříd přidružení s tabulkami, určíte pole nebo vlastnosti představují sloupce databáze. Pro tento účel [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definuje <xref:System.Data.Linq.Mapping.ColumnAttribute> atributů, jako v následujícím příkladu:  
  
### <a name="example"></a>Příklad  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 Pouze polí a vlastností namapovaných na sloupce jsou zachované nebo načtena z databáze. Ty nejsou deklarovány jako sloupce se považují za přechodná části vaší aplikace logiky.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> Atribut má celou řadu vlastností, které vám umožní přizpůsobit tyto členy, které představují sloupce (například určit členy jako představující sloupec primárního klíče). Další informace najdete v části atribut sloupce v [založených na atributech mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>Technologie LINQ to SQL přidružení a vztahy cizího klíče databáze  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], představují přidružení databáze (například cizího klíče na primární klíč relace) s použitím <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut. V následující segment kódu `Order` obsahuje třídy `Customer` vlastnost, která má <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut. Tato vlastnost a jeho atribut poskytují `Order` třídy s relací k `Customer` třídy.  
  
 Následující příklad kódu ukazuje `Customer` vlastnost z `Order` třídy.  
  
### <a name="example"></a>Příklad  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 Další informace najdete v části atribut přidružení v [založených na atributech mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>Technologie LINQ to SQL metody a databáze uložené procedury  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje uložených procedur a uživatelem definované funkce. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], mapovat tato abstrakce databáze definované objekty klienta tak, aby k dispozici v podobě silného typu z klientského kódu. Podpisy metod se podobají co možná nejvíce podpisy procedur a funkcí definovaných v databázi. Technologie IntelliSense můžete použít ke zjištění těchto metod.  
  
 Výsledek, který je nastavena vrácen voláním pro mapovanou procedury je kolekce silného typu.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje uložených procedur a funkcí na metody pomocí <xref:System.Data.Linq.Mapping.FunctionAttribute> a <xref:System.Data.Linq.Mapping.ParameterAttribute> atributy. Metody představující uložené procedury jsou odlišeny od těch, které představují uživatelem definované funkce ve <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> vlastnost. Pokud je tato vlastnost nastavená na `false` (výchozí), metoda představuje uloženou proceduru. Pokud je nastavena na `true`, metoda představuje funkci databáze.  
  
> [!NOTE]
>  Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vytvoření metody, které jsou namapované na uložených procedurách a uživatelem definované funkce.  
  
### <a name="example"></a>Příklad  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 Další informace najdete v částech funkce atribut, uložené procedury atribut a atribut parametru [založených na atributech mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) a [uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Viz také:

- [Mapování na základě atributů](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
