---
title: Odvozování tabulek
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 2c2a93d413f301dc3006b701e4bc7979a3fa7a1d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181828"
---
# <a name="inferring-tables"></a>Odvozování tabulek
Po odvození schématu pro <xref:System.Data.DataSet> z dokumentu XML, ADO.NET nejdřív zjistí prvky XML, které představují tabulky. Tabulka pro za následek následující struktury XML **datovou sadu** schématu:  
  
-   Elementy s atributy  
  
-   Elementů s podřízenými prvky  
  
-   Opakující se elementy  
  
## <a name="elements-with-attributes"></a>Elementy s atributy  
 Prvky, které mají atributy určené v nich za následek odvozené tabulky. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 Odvození proces vytvoří tabulku s názvem "Element1."  
  
 **DataSet:** Prvek DocumentElement  
  
 **Tabulka:** element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1||  
|value2|Text1|  
  
## <a name="elements-with-child-elements"></a>Elementů s podřízenými prvky  
 Prvky, které mají podřízené prvky výsledek v odvozené tabulky. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 Odvození proces vytvoří tabulku s názvem "Element1."  
  
 **DataSet:** Prvek DocumentElement  
  
 **Tabulka:** element1  
  
|ChildElement1|  
|-------------------|  
|Text1|  
  
 Dokumentu nebo kořenový element výsledek odvozené tabulky, pokud má atributy nebo podřízené prvky, které jsou odvozeny jako sloupce. Pokud má element dokumentu žádné atributy a žádné podřízené prvky, které by odvodit jako sloupce, jako je odvozený element **datovou sadu**. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 Odvození proces vytvoří tabulku s názvem "Prvek DocumentElement."  
  
 **DataSet:** NewDataSet  
  
 **Tabulka:** Prvek DocumentElement  
  
|element1|element2|  
|--------------|--------------|  
|Text1|Text2|  
  
 Vezměte v úvahu taky následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Odvození proces vytvoří **datovou sadu** s názvem "Prvek DocumentElement", který obsahuje tabulku s názvem "Element1."  
  
 **DataSet:** Prvek DocumentElement  
  
 **Tabulka:** element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="repeating-elements"></a>Opakující se elementy  
 Prvky, které opakují výsledek v jedné odvozené tabulky. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Odvození proces vytvoří tabulku s názvem "Element1."  
  
 **DataSet:** Prvek DocumentElement  
  
 **Tabulka:** element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
## <a name="see-also"></a>Viz také:

- [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
