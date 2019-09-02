---
title: Odvozování tabulek
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 84cee828f2d3c918a12e449da5b01a3d72d86333
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203517"
---
# <a name="inferring-tables"></a>Odvozování tabulek
Při odvozování schématu pro <xref:System.Data.DataSet> z dokumentu XML ADO.NET nejprve Určuje, které elementy XML reprezentují tabulky. Následující struktury XML vedou v tabulce pro schéma **datové sady** :  
  
- Elementy s atributy  
  
- Prvky s podřízenými prvky  
  
- Opakující se elementy  
  
## <a name="elements-with-attributes"></a>Elementy s atributy  
 Prvky, které mají v nich atributy, mají za následek odvozené tabulky. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem "Element1".  
  
 **Integrován** DocumentElement  
  
 **Stolní** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|Hodnota1||  
|Argument|Text1|  
  
## <a name="elements-with-child-elements"></a>Prvky s podřízenými prvky  
 Elementy, které mají podřízené elementy, mají za následek odvozené tabulky. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem "Element1".  
  
 **Integrován** DocumentElement  
  
 **Stolní** Element1  
  
|ChildElement1|  
|-------------------|  
|Text1|  
  
 Pokud obsahuje atributy nebo podřízené elementy, které jsou odvozeny jako sloupce, je výsledkem dokumentu nebo kořenového prvku odvozená tabulka. Pokud element dokumentu nemá žádné atributy a žádné podřízené prvky, které by byly odvozeny jako sloupce, je element odvozen jako **datová sada**. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem "DocumentElement".  
  
 **Integrován** NewDataSet  
  
 **Stolní** DocumentElement  
  
|Element1|Element2|  
|--------------|--------------|  
|Text1|Text2|  
  
 Případně zvažte následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří datovou **sadu** s názvem "DocumentElement", která obsahuje tabulku s názvem "Element1".  
  
 **Integrován** DocumentElement  
  
 **Stolní** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|Hodnota1|Argument|  
  
## <a name="repeating-elements"></a>Opakující se elementy  
 Prvky, které se opakují, v jedné odvozené tabulce. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem "Element1".  
  
 **Integrován** DocumentElement  
  
 **Stolní** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
## <a name="see-also"></a>Viz také:

- [Odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md)
- [Načtení datové sady z XML](loading-a-dataset-from-xml.md)
- [Načtení informací o schématu datové sady z XML](loading-dataset-schema-information-from-xml.md)
- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
