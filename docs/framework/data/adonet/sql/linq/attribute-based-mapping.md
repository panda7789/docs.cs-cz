---
title: Mapování na základě atributů
ms.date: 03/30/2017
ms.assetid: 6dd89999-f415-4d61-b8c8-237d23d7924e
ms.openlocfilehash: d7d7c14ca12e40af643d164069cf7b0f3165fa20
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223560"
---
# <a name="attribute-based-mapping"></a>Mapování na základě atributů
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] databáze SQL serveru se mapuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model buď použití atributů nebo pomocí externího mapování souboru. Toto téma popisuje, jak přístup založený na atributu.  
  
 Většina základních formou [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje databáze do <xref:System.Data.Linq.DataContext>, tabulka, která má třídu a sloupce a relace na vlastnosti na tyto třídy. Můžete také použít atributy k mapování hierarchie dědičnosti v objektovém modelu. Další informace najdete v tématu [jak: Generování objektového modelu v jazyce Visual Basic nebo C# ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
 Vývojáři obvykle pomocí sady Visual Studio provádět pomocí založených na atributech mapování [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Můžete také použít nástroj příkazového řádku SQLMetal, nebo můžete ručně kód atributy sami. Další informace najdete v tématu [jak: Generování objektového modelu v jazyce Visual Basic nebo C# ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
> [!NOTE]
>  Můžete také namapovat pomocí externího souboru XML. Další informace najdete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 Následující části popisují založených na atributech mapování podrobněji. Další informace najdete v tématu <xref:System.Data.Linq.Mapping> oboru názvů.  
  
## <a name="databaseattribute-attribute"></a>Atribut DatabaseAttribute  
 Tento atribut lze použijte k určení výchozí název databáze, pokud není zadán název připojení. Tento atribut je volitelný, ale když ho používáte, musíte použít <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost, jak je popsáno v následující tabulce.  
  
|Vlastnost|Type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|String|V tématu <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|Použít s jeho <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost určuje název databáze.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.DatabaseAttribute>.  
  
## <a name="tableattribute-attribute"></a>Atribut TableAttribute  
 Tento atribut lze použijte k určení třídy jako třídu entity, která souvisí s databázové tabulky nebo zobrazení. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zpracovává tříd, které mají tento atribut jako trvalé třídy. V následující tabulce jsou popsány <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> vlastnost.  
  
|Vlastnost|Type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>|String|Stejný řetězec jako název třídy|Určuje třídu jako třídu entity přidružené k databázové tabulky.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
## <a name="columnattribute-attribute"></a>Atribut ColumnAttribute  
 Tento atribut slouží k určení členem třídu entity k reprezentaci sloupce v databázové tabulce. Tento atribut lze použít k žádnému poli nebo vlastnosti.  
  
 Pouze ty členy identifikovat podle sloupce se načte a zachovat při [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uloží změny do databáze. Členové bez tohoto atributu jsou považovány za dočasné a nejsou odeslané k vložení nebo aktualizace.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>|AutoSync|Nikdy|Dává pokyn common language runtime (CLR) k načtení hodnoty po operaci insert nebo update.<br /><br /> Možnosti: Vždy nikdy OnUpdate, OnInsert.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>|Boolean|`true`|Označuje, že sloupec může obsahovat hodnoty null.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>|String|Typ sloupce odvozené databáze|Pomocí databáze typů a modifikátory Určuje typ sloupce databáze.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>|String|prázdný|Definuje počítaný sloupec v databázi.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>|Boolean|`false`|Označuje, že sloupec obsahuje hodnoty, které automaticky generuje databáze.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>|Boolean|`false`|Označuje, že sloupec obsahuje hodnotu diskriminátoru [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] hierarchii dědičnosti.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>|Boolean|`false`|Určuje, že tento člen třídy představuje sloupci, který je nebo je součástí primárního klíče tabulky.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>|Boolean|`false`|Určuje typ sloupce člena jako číslo časového razítka nebo verze databáze.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>|UpdateCheck|`Always`, pokud <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> je `true` pro člena|Určuje, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] blíží zjišťování konfliktů optimistického řízení souběžnosti.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
> [!NOTE]
>  Hodnoty vlastností AssociationAttribute a ColumnAttribute úložiště jsou malá a velká písmena. Například Ujistěte se, že hodnoty atributu pro vlastnost AssociationAttribute.Storage rozlišovat velikost písmen pro odpovídající názvy vlastností používá jinde v kódu. To platí pro všechny programovací jazyky .NET, včetně těch, které nejsou obvykle velká a malá písmena, včetně jazyka Visual Basic. Další informace o vlastnosti úložiště najdete v tématu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="associationattribute-attribute"></a>Atribut AssociationAttribute  
 Tento atribut slouží k určení vlastností k vyjádření přidružení v databázi, jako jsou cizí klíč pro vztah primární klíče. Další informace o relacích najdete v tématu [jak: Mapování databázových relace](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteOnNull%2A>|Boolean|`false`|Při umístění na přidružení obsahující cizí klíče jsou všechny Null, odstraní objekt při přidružení je nastavena na hodnotu null.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteRule%2A>|String|Žádné|Přidá chování při odstraňování přidružení.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsForeignKey%2A>|Boolean|`false`|Při hodnotě true se označí jako cizí klíč v přidružení reprezentující relaci databáze člena.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsUnique%2A>|Boolean|`false`|Při hodnotě true označuje omezení jedinečnosti pro cizí klíč.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A>|String|ID související třídy|Jednoho nebo více členů třídy cílové entity označí jako klíčové hodnoty na druhé straně asociace.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.ThisKey%2A>|String|ID obsažené třídy|Určuje členy této třídy entity k reprezentaci hodnoty klíče na této straně asociace.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.AssociationAttribute>.  
  
> [!NOTE]
>  Hodnoty vlastností AssociationAttribute a ColumnAttribute úložiště jsou malá a velká písmena. Například Ujistěte se, že hodnoty atributu pro vlastnost AssociationAttribute.Storage rozlišovat velikost písmen pro odpovídající názvy vlastností používá jinde v kódu. To platí pro všechny programovací jazyky .NET, včetně těch, které nejsou obvykle velká a malá písmena, včetně jazyka Visual Basic. Další informace o vlastnosti úložiště najdete v tématu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="inheritancemappingattribute-attribute"></a>Atribut InheritanceMappingAttribute  
 Tento atribut slouží k mapování hierarchie dědičnosti.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>|String|Žádné Musí být zadána hodnota.|Určuje kód hodnotu diskriminátoru.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>|Boolean|`false`|Při hodnotě true se vytvoří instanci objektu tohoto typu, pokud žádná hodnota diskriminátoru v úložišti shoduje s některou ze zadaných hodnot.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>|Type|Žádné Musí být zadána hodnota.|Určuje typ třídy v hierarchii.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>.  
  
## <a name="functionattribute-attribute"></a>Atribut FunctionAttribute  
 Tento atribut lze použijte k označení metody jako uloženou proceduru nebo uživatelem definovanou funkci v databázi.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A>|Boolean|`false`|Pokud má hodnotu false, označuje mapování uložené proceduře. Při hodnotě true označuje mapování pro uživatelem definované funkce.|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.Name%2A>|String|Stejný řetězec jako název databáze|Určuje název uložená procedura nebo uživatelem definované funkce.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.FunctionAttribute>.  
  
## <a name="parameterattribute-attribute"></a>Atribut ParameterAttribute  
 Tento atribut slouží k mapování vstupní parametry pro uložené procedury metody.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.DbType%2A>|String|Žádné|Určuje typ databáze.|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.Name%2A>|String|Stejný řetězec jako název parametru v databázi|Určuje název parametru.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ParameterAttribute>.  
  
## <a name="resulttypeattribute-attribute"></a>Atribut ResultTypeAttribute  
 Pomocí tohoto atributu zadejte typ výsledku.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ResultTypeAttribute.Type%2A>|Type|(Žádné)|Použít pro metody namapovaných na uložené procedury, které vracejí <xref:System.Data.Linq.IMultipleResults>. Deklaruje platné nebo očekávaný typ mapování pro uloženou proceduru.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ResultTypeAttribute>.  
  
## <a name="dataattribute-attribute"></a>Atribut DataAttribute  
 Pomocí tohoto atributu zadejte názvy a polí privátního úložiště.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|Type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>|String|Stejný jako název databáze|Určuje název tabulky, sloupce a tak dále.|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>|String|Veřejnou přistupující objekty|Určuje název podkladové pole úložiště.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.DataAttribute>.  
  
## <a name="see-also"></a>Viz také:

- [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
