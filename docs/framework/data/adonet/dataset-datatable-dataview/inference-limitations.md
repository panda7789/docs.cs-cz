---
title: Odvození omezení
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 308d2ffdd9e2cb16626861e25613657f341a4ccb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879642"
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
  
 **DataSet:** Prvek DocumentElement  
  
 **Tabulka:** element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 Ale pro "Document2," vytvoří procesu odvození **datovou sadu** s názvem "NewDataSet" a tabulku s názvem "Prvek DocumentElement." "Element1" je odvozen jako sloupec, protože nemá žádné atributy a žádné podřízené prvky.  
  
 **DataSet:** NewDataSet  
  
 **Tabulka:** Prvek DocumentElement  
  
|element1|  
|--------------|  
|Text1|  
  
 Tyto dva dokumenty XML byl asi zamýšlený k vytvoření stejné schéma, ale procesu odvození vytváří velmi odlišné výsledky podle elementů obsažených v jednotlivých dokumentech.  
  
 Aby se zabránilo nedostatky, které mohou nastat při generování schématu z dokumentu XML, doporučujeme explicitně zadat pomocí jazyka pro definici schématu XML (XSD) nebo XML-Data Reduced (XDR) při načítání schématu **datovou sadu** z SOUBOR XML. Další informace o explicitním zadáním **datovou sadu** schéma pomocí schématu XML, naleznete v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Viz také:

- [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
