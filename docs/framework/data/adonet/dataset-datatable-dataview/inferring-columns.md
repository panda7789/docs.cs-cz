---
title: "Odvození sloupce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 858a23fb8fec7b7f2eee95a1365d16e846beb548
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-columns"></a>Odvození sloupce
Po ADO.NET určil z dokumentu XML prvky, které k odvození jako tabulky pro <xref:System.Data.DataSet>, pak odvozeny sloupce pro tyto tabulky. ADO.NET 2.0 zavedl nový modul odvození schématu, odvodí typ silného typu dat pro každou **simpleType** elementu. V předchozích verzích, datový typ odvozené **simpleType** element byla vždy **xsd:string**.  
  
## <a name="migration-and-backward-compatibility"></a>Migrace a zpětná kompatibilita  
 **ReadXml** metoda přebírá argument typu **InferSchema**. Tento argument umožňuje zadat chování odvození kompatibilní s předchozími verzemi. Dostupné hodnoty pro **InferSchema** výčtu jsou uvedeny v následující tabulce.  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 Poskytuje zpětné kompatibility tím, že vždy odvození jednoduchý typ. jako <xref:System.String>.  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 Odvodí typ dat silného typu. Vyvolá výjimku, pokud se používá s <xref:System.Data.DataTable>.  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 Ignoruje všechny vložené schéma a čte data do existujících <xref:System.Data.DataSet> schématu.  
  
## <a name="attributes"></a>Atributy  
 Jak jsou definovány v [odvození tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), bude ji odvodit element s atributy, jako tabulku. Atributy tohoto prvku bude potom odvodit jako sloupce pro tabulku. **ColumnMapping** vlastnost sloupců bude nastavena pro **MappingType.Attribute**, aby bylo zajištěno, že názvy sloupců zapisovat jako atributy, pokud schéma se nezapisují zpět do formátu XML. Hodnoty atributů jsou uložené v řádku v tabulce. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci, **attr1** a **attr2**. **ColumnMapping** vlastnost oba sloupce bude nastavena pro **MappingType.Attribute**.  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>Elementy bez atributy nebo podřízené elementy  
 Pokud element má žádné podřízené elementy nebo atributy, bude odvodit jako sloupec. **ColumnMapping** vlastnost sloupec bude nastavena pro **MappingType.Element**. Text pro podřízené elementy je uložen v řádku v tabulce. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci, **ChildElement1** a **ChildElement2**. **ColumnMapping** vlastnost oba sloupce bude nastavena pro **MappingType.Element**.  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## <a name="see-also"></a>Viz také  
 [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
