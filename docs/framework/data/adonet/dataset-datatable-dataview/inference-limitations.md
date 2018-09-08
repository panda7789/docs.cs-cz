---
title: Odvození omezení
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: d113df98cdd339300b3e75ceda49a56d4f346d3c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190675"
---
# <a name="inference-limitations"></a>Odvození omezení
Proces odvození <xref:System.Data.DataSet> schéma ze souboru XML může vést k různými schématy v závislosti na prvky XML v jednotlivých dokumentech. Představte si třeba následující dokumenty XML.  
  
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
  
 Pro "Dokument1," vytvoří procesu odvození **datovou sadu** s názvem "Prvek DocumentElement" a tabulku s názvem "Element1", "Element1" představuje opakující se prvek proto.  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 Ale pro "Document2," vytvoří procesu odvození **datovou sadu** s názvem "NewDataSet" a tabulku s názvem "Prvek DocumentElement." "Element1" je odvozen jako sloupec, protože nemá žádné atributy a žádné podřízené prvky.  
  
 **Datová sada:** NewDataSet  
  
 **Tabulka:** prvek DocumentElement  
  
|element1|  
|--------------|  
|Text1|  
  
 Tyto dva dokumenty XML byl asi zamýšlený k vytvoření stejné schéma, ale procesu odvození vytváří velmi odlišné výsledky podle elementů obsažených v jednotlivých dokumentech.  
  
 Aby se zabránilo nedostatky, které mohou nastat při generování schématu z dokumentu XML, doporučujeme explicitně zadat pomocí jazyka pro definici schématu XML (XSD) nebo XML-Data Reduced (XDR) při načítání schématu **datovou sadu** z SOUBOR XML. Další informace o explicitním zadáním **datovou sadu** schéma pomocí schématu XML, naleznete v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Viz také  
 [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
