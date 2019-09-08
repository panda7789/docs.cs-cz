---
title: Objektový model LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: b73904e2347c501b21b2c5933d0b43c7abafeb7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792309"
---
# <a name="the-linq-to-sql-object-model"></a>Objektový model LINQ to SQL
V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]portálu je objektový model vyjádřený v programovacím jazyce vývojáře mapován na datový model relační databáze. Operace s daty se pak provádí v závislosti na objektovém modelu.  
  
 V tomto scénáři nebudete k databázi dávat příkazy databáze (například `INSERT`). Místo toho můžete změnit hodnoty a spustit metody v rámci modelu objektu. Pokud se chcete dotazovat databáze nebo odeslat změny, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přeloží vaše požadavky na správné příkazy SQL a odešle tyto příkazy do databáze.  
  
 ![Snímek obrazovky, který zobrazuje model objektu LINQ.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 Nejzákladnější prvky v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektovém modelu a jejich vztah k prvkům v modelu relačních dat jsou shrnuty v následující tabulce:  
  
|Model objektu LINQ to SQL|Relační datový model|  
|------------------------------|---------------------------|  
|Třída entity|Tabulka|  
|Člen třídy|Sloupec|  
|Řídí|Vztah cizího klíče|  
|Metoda|Uložená procedura nebo funkce|  
  
> [!NOTE]
> Následující popisy předpokládají, že máte základní znalosti modelu relačních dat a pravidel.  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a>LINQ to SQL třídy entit a databázových tabulek  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nástroji je databázová tabulka reprezentovaná *třídou entity*. Třída entity se podobá jakékoli jiné třídě, kterou můžete vytvořit s výjimkou toho, že třídu přiřadíte pomocí speciálních informací, které přidruží třídu k databázové tabulce. Tuto poznámku uděláte přidáním vlastního atributu (<xref:System.Data.Linq.Mapping.TableAttribute>) do deklarace třídy, jako v následujícím příkladu:  
  
### <a name="example"></a>Příklad  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 Do databáze mohou být uloženy pouze instance tříd deklarované jako tabulky (tj. třídy entit).  
  
 Další informace naleznete v části atribut tabulky [mapování na základě atributů](attribute-based-mapping.md).  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a>LINQ to SQL členů třídy a databázových sloupců  
 Kromě přidružení tříd k tabulkám určíte pole nebo vlastnosti, které budou představovat sloupce databáze. Pro tento účel [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> definuje atribut, jako v následujícím příkladu:  
  
### <a name="example"></a>Příklad  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 Z databáze jsou trvala nebo načtena pouze pole a vlastnosti mapované na sloupce. Ty, které nejsou deklarovány jako sloupce, se považují za přechodné části logiky aplikace.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> Atribut má celou řadu vlastností, které lze použít k přizpůsobení těchto členů, kteří představují sloupce (například určení člena představujícího sloupec primárního klíče). Další informace naleznete v části atribut sloupce [mapování na základě atributů](attribute-based-mapping.md).  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a>LINQ to SQL přidružení a relace cizího klíče databáze  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nástroji představujete přidružení databáze (například relace cizího klíče k primárním klíčům) <xref:System.Data.Linq.Mapping.AssociationAttribute> použitím atributu. V následujícím segmentu kódu `Order` třída `Customer` obsahuje vlastnost, která má <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut. Tato vlastnost a její atribut poskytují `Order` třídu s relací `Customer` ke třídě.  
  
 Následující příklad kódu ukazuje `Customer` vlastnost `Order` z třídy.  
  
### <a name="example"></a>Příklad  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 Další informace naleznete v části atributu přidružení v [mapování na základě atributů](attribute-based-mapping.md).  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a>Metody LINQ to SQL a uložené procedury databáze  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje uložené procedury a uživatelsky definované funkce. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nástroji namapujete tyto abstrakce definované databáze na objekty klienta, abyste k nim měli přístup pomocí silného typu z klientského kódu. Signatury metody se podobají co nejpřesněji těm podpisům procedur a funkcí, které jsou definovány v databázi. Pomocí technologie IntelliSense můžete tyto metody zjistit.  
  
 Sada výsledků vrácená voláním mapované procedury je silně typovou kolekcí.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje uložené procedury a funkce na metody pomocí <xref:System.Data.Linq.Mapping.FunctionAttribute> atributů a. <xref:System.Data.Linq.Mapping.ParameterAttribute> Metody představující uložené procedury jsou odlišeny od těch, které představují uživatelsky definované <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> funkce vlastností. Pokud je tato vlastnost nastavena na `false` (výchozí), metoda představuje uloženou proceduru. Pokud je nastaveno na `true`, metoda představuje funkci databáze.  
  
> [!NOTE]
> Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů k vytvoření metod mapovaných na uložené procedury a uživatelsky definované funkce.  
  
### <a name="example"></a>Příklad  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 Další informace naleznete v částech atribut funkce, atribut uložené procedury a atributů parametrů [mapování založeného na atributech](attribute-based-mapping.md) a [uložených procedur](stored-procedures.md).  
  
## <a name="see-also"></a>Viz také:

- [Mapování na základě atributů](attribute-based-mapping.md)
- [Základní informace](background-information.md)
