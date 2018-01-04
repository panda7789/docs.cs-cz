---
title: "Technologie LINQ to SQL objektový Model"
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
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1ecccda5b9570519f69cadc9214daded16edbc89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="the-linq-to-sql-object-model"></a>Technologie LINQ to SQL objektový Model
V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vyjádřené v programovací jazyk vývojář objektový model je namapována na datový model relační databáze. Operace s daty jsou pak provedeny podle modelu objektu.  
  
 V tomto scénáři není vydávat příkazy databáze (například `INSERT`) do databáze. Místo toho můžete změnit hodnoty a spouštět metody v rámci objektu modelu. Pokud chcete dotaz na databázi nebo odeslání se změní, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá své žádosti do správné příkazy SQL a odešle tyto příkazy do databáze.  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Většina základních elementů v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model a jejich vztahu k elementů ve model relačních dat jsou shrnuty v následující tabulce:  
  
|Technologie LINQ to SQL objektový Model|Relační datový Model|  
|------------------------------|---------------------------|  
|Třídy entita|Tabulka|  
|Člen třídy|Sloupec|  
|Přidružení|Cizí klíč relace|  
|Metoda|Uložená procedura nebo funkce|  
  
> [!NOTE]
>  V následujících popisech Předpokládejme, že máte základní znalosti o relační datový model a pravidla.  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>Technologie LINQ to SQL Entity třídy a tabulek databáze  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], databázové tabulky je reprezentována *třídy entita*. Třídu entity je jako jiné třídy, které můžete vytvořit s tím rozdílem, že přidání poznámek ke třídě pomocí speciální informace, které přidružuje třída databázové tabulky. Tato anotace provést přidáním vlastních atributů (<xref:System.Data.Linq.Mapping.TableAttribute>) do vaší deklaraci třídy, jako v následujícím příkladu:  
  
### <a name="example"></a>Příklad  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 Pouze instance tříd deklarovaných jako tabulky (to znamená, tříd entit) lze uložit do databáze.  
  
 Další informace najdete v části atribut tabulky z [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>Technologie LINQ to SQL členy třídy a sloupců databáze  
 Kromě přiřazení třídy s tabulkami, určete pole nebo vlastnosti představují sloupců databáze. Pro tento účel [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] definuje <xref:System.Data.Linq.Mapping.ColumnAttribute> atributů, jako v následujícím příkladu:  
  
### <a name="example"></a>Příklad  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 Pouze polí a vlastností namapovaných na sloupce jsou uchovány v nebo načíst z databáze. Ty není deklarován jako sloupce jsou považovány za jako přechodný částí logiky aplikace.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> Atribut má celou řadu vlastností, které můžete použít k přizpůsobení těchto členů, které představují sloupce (například určení člena jako představující sloupec primárního klíče). Další informace najdete v části atribut sloupce [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>Technologie LINQ to SQL přidružení a relace cizího klíče databáze  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], představují přidružení databáze (například cizího klíče do primárního klíče relace) s použitím <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut. V následující segmentu kódu `Order` třída obsahuje `Customer` vlastnost, která má <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut. Tato vlastnost a jeho atribut poskytují `Order` třídy s relací k `Customer` třídy.  
  
 Následující příklad kódu ukazuje `Customer` vlastnost z `Order` třídy.  
  
### <a name="example"></a>Příklad  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 Další informace najdete v tématu části přidružení atribut [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>Technologie LINQ to SQL metody a databáze uložené procedury  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje uložené procedury a funkce definované uživatelem. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], mapování těchto abstrakce definované databáze na objekty klienta, aby přístup jim silného typu způsobem z kódu klienta. Metoda podpisy podobat co možná nejvíce signatur procedury a funkce, které jsou definované v databázi. IntelliSense můžete použít ke zjištění těchto metod.  
  
 Výsledek, který je nastaven vrácené voláním namapované proceduře je silného typu kolekce.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje uložené procedury a funkce metody pomocí <xref:System.Data.Linq.Mapping.FunctionAttribute> a <xref:System.Data.Linq.Mapping.ParameterAttribute> atributy. Metody představující uložené procedury rozlišují od těch, představující uživatelsky definované funkce pomocí <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> vlastnost. Pokud je tato vlastnost nastavena na `false` (výchozí), metoda představuje uložené procedury. Pokud je nastaven na hodnotu `true`, metoda představuje funkce databáze.  
  
> [!NOTE]
>  Pokud používáte [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vytvoření metody, které jsou namapované na uložené procedury a uživatelem definované funkce.  
  
### <a name="example"></a>Příklad  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 Další informace najdete v tématu na atribut funkce, uložené procedury atribut a atribut parametru části [na základě atributů mapování](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) a [uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Viz také  
 [Mapování na základě atributů](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
