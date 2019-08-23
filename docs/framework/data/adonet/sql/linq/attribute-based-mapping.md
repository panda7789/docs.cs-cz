---
title: Mapování na základě atributů
ms.date: 03/30/2017
ms.assetid: 6dd89999-f415-4d61-b8c8-237d23d7924e
ms.openlocfilehash: 41152aa81ab84a2ab77e9a4ebf16e102ee5c0e3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964096"
---
# <a name="attribute-based-mapping"></a>Mapování na základě atributů
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje databázi SQL Server na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektový model buď použitím atributů, nebo pomocí externího mapovacího souboru. Toto téma popisuje přístup založený na atributech.  
  
 Ve své nejvíc základní formě [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje databázi <xref:System.Data.Linq.DataContext>na, tabulku na třídu a sloupce a relace na vlastnosti těchto tříd. Můžete také použít atributy k mapování hierarchie dědičnosti v objektovém modelu. Další informace najdete v tématu [jak: Vygenerujte objektový model v Visual Basic nebo C# ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
 Vývojáři, kteří používají Visual Studio, obvykle provádějí mapování na základě atributů pomocí Návrhář relací objektů. Můžete také použít nástroj příkazového řádku SQLMetal, nebo můžete atributy ručně zakódovat. Další informace najdete v tématu [jak: Vygenerujte objektový model v Visual Basic nebo C# ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
> [!NOTE]
> Můžete také mapovat pomocí externího souboru XML. Další informace najdete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 Následující části popisují mapování na základě atributů podrobněji. Další informace najdete v <xref:System.Data.Linq.Mapping> tématu obor názvů.  
  
## <a name="databaseattribute-attribute"></a>DatabaseAttribute – atribut  
 Tento atribut slouží k určení výchozího názvu databáze, pokud není název dodán připojením. Tento atribut je nepovinný, ale pokud ho použijete, musíte použít <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost, jak je popsáno v následující tabulce.  
  
|Vlastnost|type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|String|Si<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|Používá se s <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastností, určuje název databáze.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.DatabaseAttribute>.  
  
## <a name="tableattribute-attribute"></a>TableAttribute – atribut  
 Tento atribut použijte k označení třídy jako třídy entity, která je přidružena k databázové tabulce nebo zobrazení. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zpracovává třídy, které mají tento atribut jako trvalé třídy. V následující tabulce je <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> popsána vlastnost.  
  
|Vlastnost|type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>|String|Stejný řetězec jako název třídy|Určí třídu jako třídu entity přidruženou k databázové tabulce.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
## <a name="columnattribute-attribute"></a>ColumnAttribute – atribut  
 Tento atribut slouží k určení člena třídy entity představující sloupec v databázové tabulce. Tento atribut lze použít pro jakékoli pole nebo vlastnost.  
  
 Při [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ukládání změn do databáze jsou načteny a uchovány pouze členové, které jste identifikovali jako sloupce. U členů bez tohoto atributu se předpokládá, že nejsou trvalé a nejsou odeslány pro příkazy INSERT a Update.  
  
 Následující tabulka obsahuje popis vlastností tohoto atributu.  
  
|Vlastnost|type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>|AutoSync|Nikdy|Instruuje modul CLR (Common Language Runtime), aby načetl hodnotu po operaci INSERT nebo Update.<br /><br /> Nastavení Always, nikdy, Update, INSERT.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>|Boolean|`true`|Označuje, že sloupec může obsahovat hodnoty null.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>|String|Odvozený typ databázového sloupce|Používá typy a modifikátory databáze k určení typu sloupce databáze.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>|String|Obsahovat|Definuje vypočítaný sloupec v databázi.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>|Boolean|`false`|Indikuje, že sloupec obsahuje hodnoty, které databáze automaticky generuje.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>|Boolean|`false`|Označuje, že sloupec obsahuje hodnotu diskriminátoru pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] hierarchii dědičnosti.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>|Boolean|`false`|Určuje, že tento člen třídy představuje sloupec, který je nebo je součástí primárních klíčů tabulky.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>|Boolean|`false`|Identifikuje typ sloupce člena jako časové razítko nebo číslo verze databáze.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>|UpdateCheck|`Always`, pokud <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> není `true` pro člena|Určuje, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jak přístupy k detekci optimistických konfliktů při souběžnosti.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
> [!NOTE]
> Hodnoty vlastností úložiště AssociationAttribute a ColumnAttribute rozlišují velká a malá písmena. Například zajistěte, aby hodnoty použité v atributu vlastnosti AssociationAttribute. Storage odpovídaly velikosti písmen pro odpovídající názvy vlastností používané jinde v kódu. To platí pro všechny programovací jazyky rozhraní .NET, i ty, které se obvykle nerozlišují bez rozlišení velkých a malých písmen, včetně Visual Basic. Další informace o vlastnosti úložiště naleznete v tématu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="associationattribute-attribute"></a>AssociationAttribute – atribut  
 Pomocí tohoto atributu určíte vlastnost, která představuje přidružení v databázi, jako je cizí klíč vztahu k primárnímu klíči. Další informace o relacích najdete v [tématu How to: Mapování databázových](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)vztahů.  
  
 Následující tabulka obsahuje popis vlastností tohoto atributu.  
  
|Vlastnost|type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteOnNull%2A>|Boolean|`false`|Při umístění na přidružení, jehož členové cizího klíče jsou neumožňující hodnotu null, odstraní objekt, když je přidružení nastaveno na hodnotu null.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteRule%2A>|String|Žádné|Přidá chování při odstraňování do přidružení.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsForeignKey%2A>|Boolean|`false`|Pokud má hodnotu true, určí člena jako cizí klíč v přidružení představující relaci databáze.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsUnique%2A>|Boolean|`false`|Pokud má hodnotu true, označuje pro cizí klíč omezení jedinečnosti.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A>|String|ID související třídy|Určuje jednoho nebo více členů třídy cílové entity jako klíčové hodnoty na druhé straně přidružení.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.ThisKey%2A>|String|ID obsahující třídy|Určuje členy této třídy entity, které reprezentují klíčové hodnoty na této straně přidružení.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.AssociationAttribute>.  
  
> [!NOTE]
> Hodnoty vlastností úložiště AssociationAttribute a ColumnAttribute rozlišují velká a malá písmena. Například zajistěte, aby hodnoty použité v atributu vlastnosti AssociationAttribute. Storage odpovídaly velikosti písmen pro odpovídající názvy vlastností používané jinde v kódu. To platí pro všechny programovací jazyky rozhraní .NET, i ty, které se obvykle nerozlišují bez rozlišení velkých a malých písmen, včetně Visual Basic. Další informace o vlastnosti úložiště naleznete v tématu <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="inheritancemappingattribute-attribute"></a>InheritanceMappingAttribute – atribut  
 Tento atribut použijte k mapování hierarchie dědičnosti.  
  
 Následující tabulka obsahuje popis vlastností tohoto atributu.  
  
|Vlastnost|type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>|String|Žádné Hodnota musí být dodána.|Určuje hodnotu kódu diskriminátoru.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>|Boolean|`false`|Pokud má hodnotu true, vytvoří instance objektu tohoto typu, pokud žádná hodnota diskriminátoru v úložišti neodpovídá žádné z zadaných hodnot.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>|type|Žádné Hodnota musí být dodána.|Určuje typ třídy v hierarchii.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>.  
  
## <a name="functionattribute-attribute"></a>FunctionAttribute – atribut  
 Pomocí tohoto atributu lze určit metodu, která představuje uloženou proceduru nebo uživatelsky definovanou funkci v databázi.  
  
 Následující tabulka popisuje vlastnosti tohoto atributu.  
  
|Vlastnost|type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A>|Boolean|`false`|Pokud má hodnotu false, označuje mapování na uloženou proceduru. Pokud má hodnotu true, označuje mapování na uživatelsky definovanou funkci.|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.Name%2A>|String|Stejný řetězec jako název v databázi|Určuje název uložené procedury nebo uživatelsky definované funkce.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.FunctionAttribute>.  
  
## <a name="parameterattribute-attribute"></a>ParameterAttribute – atribut  
 Tento atribut použijte k mapování vstupních parametrů na metodách uložených procedur.  
  
 Následující tabulka obsahuje popis vlastností tohoto atributu.  
  
|Vlastnost|type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.DbType%2A>|String|Žádné|Určuje typ databáze.|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.Name%2A>|String|Stejný řetězec jako název parametru v databázi|Určuje název parametru.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ParameterAttribute>.  
  
## <a name="resulttypeattribute-attribute"></a>ResultTypeAttribute – atribut  
 Tento atribut slouží k určení typu výsledku.  
  
 Následující tabulka obsahuje popis vlastností tohoto atributu.  
  
|Vlastnost|type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ResultTypeAttribute.Type%2A>|type|NTato|Používá se na metodách mapovaných na uložené <xref:System.Data.Linq.IMultipleResults>procedury, které vrací. Deklaruje platná nebo očekávaná mapování typů pro uloženou proceduru.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ResultTypeAttribute>.  
  
## <a name="dataattribute-attribute"></a>Atribut dataatributu  
 Tento atribut slouží k určení názvů a privátních polí úložiště.  
  
 Následující tabulka obsahuje popis vlastností tohoto atributu.  
  
|Vlastnost|type|Výchozí|Popis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>|String|Stejné jako název v databázi|Určuje název tabulky, sloupce a tak dále.|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>|String|Veřejné přístupové objekty|Určuje název podkladového pole úložiště.|  
  
 Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.DataAttribute>.  
  
## <a name="see-also"></a>Viz také:

- [Referenční informace](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
