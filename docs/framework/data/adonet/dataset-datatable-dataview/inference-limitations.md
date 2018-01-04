---
title: "Odvození omezení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3053d4e83233027f28357d8c45087df71c21ca18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="inference-limitations"></a>Odvození omezení
Proces odvození <xref:System.Data.DataSet> schématu z XML může mít za následek různé schémata v závislosti na elementy XML v každý dokument. Zvažte například následující dokumenty XML.  
  
 Dokument1:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 Pro "Dokument1," proces odvození vytváří **datovou sadu** s názvem "Prvek DocumentElement" a tabulka s názvem "Element1,", protože "Element1" je opakující se prvek.  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 Ale pro "Document2," vytvoří proces odvození **datovou sadu** s názvem "NewDataSet" a tabulka s názvem "Prvek DocumentElement." "Element1" je jako sloupec odvodit, protože nemá žádné atributy a žádné podřízené prvky.  
  
 **Datová sada:** NewDataSet  
  
 **Tabulka:** prvek DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 Tyto dva dokumenty XML může byla určených k vytvoření stejného schématu, ale proces odvození vytváří velmi odlišné výsledky podle elementů obsažených v každém dokumentu.  
  
 Abyste se vyhnuli rozporů může dojít, když generování schématu z dokumentu XML, doporučujeme explicitně zadáte pomocí jazyka pro definici schématu XML (XSD) nebo XML-Data Reduced (XDR) při načítání schématu **datovou sadu** z SOUBOR XML. Další informace o explicitně určit **datovou sadu** schématu se schématem XML, najdete v části [odvozování relační strukturu datové sady z schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Viz také  
 [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
