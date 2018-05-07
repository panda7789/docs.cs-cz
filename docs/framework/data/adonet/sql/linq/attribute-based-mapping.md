---
title: Na základě atributů mapování
ms.date: 03/30/2017
ms.assetid: 6dd89999-f415-4d61-b8c8-237d23d7924e
ms.openlocfilehash: 81bbe8806694967d68c3e15da1d582092fb95e1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="attribute-based-mapping"></a>Na základě atributů mapování
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje databázi systému SQL Server k [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model buď použití atributy nebo pomocí externího mapování souboru. Toto téma popisuje přístup založený na atributu.  
  
 Většina základní formou [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje databáze do <xref:System.Data.Linq.DataContext>, tabulku pro třídu a sloupce a vztahů s vlastností na těchto třídách. Atributy můžete také použít k mapování hierarchie dědičnosti v objektovém modelu. Další informace najdete v tématu [postupy: generování objektový Model v jazyce Visual Basic nebo C#](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
 Vývojáři obvykle pomocí sady Visual Studio provádět na základě atributů mapování pomocí [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Můžete také použít nástroj příkazového řádku na SQLMetal, nebo můžete ručně kódu atributy sami. Další informace najdete v tématu [postupy: generování objektový Model v jazyce Visual Basic nebo C#](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
> [!NOTE]
>  Můžete také mapovat pomocí externího souboru XML. Další informace najdete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 Následující části popisují na základě atributů mapování podrobněji. Další informace najdete v tématu <xref:System.Data.Linq.Mapping> oboru názvů.  
  
## <a name="databaseattribute-attribute"></a>Atribut DatabaseAttribute  
 Tento atribut použijte k určení výchozí název databáze, když není zadaný název připojení. Tento atribut je volitelný, ale pokud chcete použít, musíte použít <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost, jak je popsáno v následující tabulce.  
  
|Vlastnost|Typ|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|String|V tématu <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|Použít s jeho <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost, určuje název databáze.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.DatabaseAttribute>.  
  
## <a name="tableattribute-attribute"></a>Atribut TableAttribute  
 Pomocí tohoto atributu lze určit třídu jako třídu entity, který je přidružen databázové tabulky nebo zobrazení. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zpracovává tříd, které mají tento atribut jako trvalé třídy. V následující tabulce jsou popsány <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> vlastnost.  
  
|Vlastnost|Typ|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>|String|Řetězec stejný jako název třídy|Určuje třídu jako třídu entity, která je přidružená k tabulce databáze.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
## <a name="columnattribute-attribute"></a>Atribut ColumnAttribute  
 Tento atribut slouží k určení členem třídu entity k reprezentaci sloupec v tabulce databáze. Tento atribut můžete použít k žádnému pole nebo vlastnost.  
  
 Pouze členové, identifikovat jako sloupce jsou načteny a jako trvalý, když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uloží změny do databáze. Členové bez tohoto atributu se předpokládá, že dočasnou a nejsou odeslané pro vložení nebo aktualizace.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Typ|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>|Funkcí automatické synchronizace|Nikdy|Dá pokyn modul CLR (CLR) k načtení hodnoty po operace insert nebo update.<br /><br /> Možnosti: Vždy, nikdy, OnUpdate, OnInsert.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>|Boolean|`true`|Označuje, že sloupec může obsahovat hodnoty null.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>|String|Typ sloupce odvozené databáze|Používá typy databáze a modifikátory k zadání typu sloupce databáze.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>|String|prázdný|Definuje počítaný sloupec v databázi.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>|Boolean|`false`|Označuje, že sloupec obsahuje hodnoty, které automaticky generuje databáze.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>|Boolean|`false`|Označuje, že sloupec obsahuje hodnotu diskriminátoru [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] hierarchie dědičnosti.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>|Boolean|`false`|Určuje, že tento člen třídy představuje sloupec, který je nebo je součástí primárního klíče v tabulce.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>|Boolean|`false`|Typ sloupce člena identifikuje jako číslo časové razítko nebo verze databáze.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>|UpdateCheck|`Always`, pokud <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> je `true` pro člena|Určuje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] blíží detekce optimistickou metodu souběžného je v konfliktu.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
> [!NOTE]
>  Hodnoty vlastností AssociationAttribute a ColumnAttribute úložiště rozlišují malá a velká písmena. Například zajistěte, že hodnoty atributu pro vlastnost AssociationAttribute.Storage malá a velká písmena pro odpovídající vlastnost názvy používá někde v kódu. To platí pro všechny programovacích jazyků .NET, včetně těch, které nejsou obvykle velká a malá písmena, včetně Visual Basic. Další informace o vlastnosti úložiště najdete v tématu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="associationattribute-attribute"></a>Atribut AssociationAttribute  
 Tento atribut slouží k určení vlastnost, která má představovat přidružení v databázi, jako jsou cizí klíč pro vztah primární klíče. Další informace o vztazích najdete v tématu [postup: mapy databáze vztahy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Typ|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteOnNull%2A>|Boolean|`false`|Při umístění na přidružení obsahující cizího klíče neumožňují všechny hodnotu Null, odstraní objekt přidružení je nastavena na hodnotu null.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteRule%2A>|String|Žádné|Přidá odstranit chování přidružení.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsForeignKey%2A>|Boolean|`false`|V případě hodnoty true označí jako cizí klíč v přidružení představující relaci databáze člena.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsUnique%2A>|Boolean|`false`|V případě hodnoty true označuje jedinečnosti omezení pro cizí klíč.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A>|String|ID související třídy|Označí jako hodnoty klíče na druhé straně přidružení jednoho nebo více členů entity cílové třídy.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.ThisKey%2A>|String|ID obsahující – třída|Označí členy této třídy entity k reprezentaci hodnoty klíče na této straně tohoto přidružení.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.AssociationAttribute>.  
  
> [!NOTE]
>  Hodnoty vlastností AssociationAttribute a ColumnAttribute úložiště rozlišují malá a velká písmena. Například zajistěte, že hodnoty atributu pro vlastnost AssociationAttribute.Storage malá a velká písmena pro odpovídající vlastnost názvy používá někde v kódu. To platí pro všechny programovacích jazyků .NET, včetně těch, které nejsou obvykle velká a malá písmena, včetně Visual Basic. Další informace o vlastnosti úložiště najdete v tématu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="inheritancemappingattribute-attribute"></a>Atribut InheritanceMappingAttribute  
 Tento atribut slouží k mapování hierarchie dědičnosti.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Typ|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>|String|Žádné Musí být zadána hodnota.|Určuje hodnotu kódu diskriminátoru.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>|Boolean|`false`|V případě hodnoty true vytvoří objekt tohoto typu, když žádná hodnota diskriminátoru v úložišti odpovídá kterákoli ze zadaných hodnot.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>|Typ|Žádné Musí být zadána hodnota.|Určuje typ třídy v hierarchii.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>.  
  
## <a name="functionattribute-attribute"></a>Atribut FunctionAttribute  
 Pomocí tohoto atributu lze určit metodu jako představující uložená procedura nebo uživatelem definovanou funkci v databázi.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Typ|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A>|Boolean|`false`|Pokud je hodnota false, označuje mapování uložené procedury. V případě hodnoty true označuje mapování na uživatelem definované funkce.|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.Name%2A>|String|Řetězec stejný jako název v databázi|Určuje název uložená procedura nebo uživatelem definované funkce.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.FunctionAttribute>.  
  
## <a name="parameterattribute-attribute"></a>Atribut ParameterAttribute  
 Tento atribut slouží k mapování vstupní parametry pro metody uložené procedury.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Typ|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.DbType%2A>|String|Žádné|Určuje typ databáze.|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.Name%2A>|String|Řetězec stejný jako název parametru v databázi|Určuje název parametru.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ParameterAttribute>.  
  
## <a name="resulttypeattribute-attribute"></a>Atribut ResultTypeAttribute  
 Tento atribut použijte k určení typu výsledek.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Typ|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ResultTypeAttribute.Type%2A>|Typ|(Žádný)|Použít na metody mapovat k uloženým procedurám, které vracejí <xref:System.Data.Linq.IMultipleResults>. Deklaruje mapování platná nebo se očekává typu pro uloženou proceduru.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ResultTypeAttribute>.  
  
## <a name="dataattribute-attribute"></a>Atribut DataAttribute  
 Tento atribut slouží k určení názvů a pole privátní úložiště.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Typ|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>|String|Stejný jako název v databázi|Určuje název tabulky, sloupce a tak dále.|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>|String|Veřejné přístupové objekty|Určuje název podkladové pole úložiště.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.DataAttribute>.  
  
## <a name="see-also"></a>Viz také  
 [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
