---
title: "Odvození tabulky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dacf3518f77067a34b0da3a8e6438b813fca3912
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="inferring-tables"></a>Odvození tabulky
Pokud schéma pro odvození <xref:System.Data.DataSet> z dokumentu XML ADO.NET nejdřív zjistí, které elementy XML představují tabulky. Následující struktury XML výsledkem tabulka pro **datovou sadu** schématu:  
  
-   Elementy s atributy  
  
-   Elementy podřízené elementy  
  
-   Opakující se elementy  
  
## <a name="elements-with-attributes"></a>Elementy s atributy  
 Prvky, které mají mít za následek zadané v nich atributy odvozené tabulky. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem "Element1."  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1||  
|Value2|Text1|  
  
## <a name="elements-with-child-elements"></a>Elementy podřízené elementy  
 Prvky, které mají výsledek podřízené elementy v odvozené tabulky. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem "Element1."  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|ChildElement1|  
|-------------------|  
|Text1|  
  
 Dokument nebo kořenové, element výsledek odvozené tabulky, pokud má atributy nebo podřízené prvky, které jsou odvozené jako sloupce. Pokud dokument prvek nemá žádné atributy a žádné podřízené prvky, které by odvodit jako sloupce, jako je odvodit elementu **datovou sadu**. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem "Prvek DocumentElement."  
  
 **Datová sada:** NewDataSet  
  
 **Tabulka:** prvek DocumentElement  
  
|Element1|Element2|  
|--------------|--------------|  
|Text1|Text2|  
  
 Případně zvažte následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Proces odvození vytváří **datovou sadu** s názvem "Prvek DocumentElement" obsahující tabulku s názvem "Element1."  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|Value2|  
  
## <a name="repeating-elements"></a>Opakující se elementy  
 Prvky, které opakujte výsledek v jedné odvozené tabulky. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem "Element1."  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
## <a name="see-also"></a>Viz také  
 [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
