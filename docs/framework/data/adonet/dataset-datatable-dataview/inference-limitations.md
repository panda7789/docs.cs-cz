---
title: Odvození omezení
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 4e0f63776162b60c9333ba47be58ea78a9b6805d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204829"
---
# <a name="inference-limitations"></a>Odvození omezení
Proces odvození <xref:System.Data.DataSet> schématu z kódu XML může mít za následek různá schémata v závislosti na prvcích XML v jednotlivých dokumentech. Zvažte například následující dokumenty XML.  
  
 Document1  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 Pro "Document1", proces odvození vytvoří datovou **sadu** s názvem "DocumentElement" a tabulku s názvem "Element1", protože "Element1" je opakující se element.  
  
 **Integrován** DocumentElement  
  
 **Stolní** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 Pro "Document2" ale proces odvození vytvoří **datovou sadu** s názvem "NewDataSet" a tabulku s názvem "DocumentElement". "Element1" je odvozen jako sloupec, protože nemá žádné atributy a žádné podřízené prvky.  
  
 **Integrován** NewDataSet  
  
 **Stolní** DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 Tyto dva dokumenty XML mohou být určeny k vytvoření stejného schématu, ale proces odvození vytváří velmi různé výsledky na základě prvků obsažených v jednotlivých dokumentech.  
  
 Aby nedocházelo ke konfliktům, ke kterým může dojít při generování schématu z dokumentu XML, doporučujeme při načítání **datové sady** z XML explicitně zadat schéma pomocí jazyka XSD (XML Schema Definition Language) nebo souboru XDR (XML – data s omezením). Další informace o explicitním určení schématu **datové sady** pomocí schématu XML naleznete v tématu [odvozování relační struktury datové sady ze schématu XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Viz také:

- [Odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md)
- [Načtení datové sady z XML](loading-a-dataset-from-xml.md)
- [Načtení informací o schématu datové sady z XML](loading-dataset-schema-information-from-xml.md)
- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
