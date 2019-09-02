---
title: Odvozování sloupců
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 651d132fd76ba9015d4730a5e519bc679608e275
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203590"
---
# <a name="inferring-columns"></a>Odvozování sloupců
Jakmile ADO.NET zjistí z dokumentu XML <xref:System.Data.DataSet>, které prvky mají být odvozeny jako tabulky pro,, pak odvodí sloupce pro tyto tabulky. ADO.NET 2,0 představil nový modul odvození schématu, který odvodí datový typ silného typu pro každý element **simpleType** . V předchozích verzích byl datový typ odvozeného elementu **simpleType** vždy **xsd: String**.  
  
## <a name="migration-and-backward-compatibility"></a>Migrace a zpětná kompatibilita  
 Metoda **ReadXml** přebírá argument typu **InferSchema**. Tento argument umožňuje určit chování při odvozování kompatibilní s předchozími verzemi. Dostupné hodnoty pro výčet **InferSchema** jsou uvedeny v následující tabulce.  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 Poskytuje zpětnou kompatibilitu tím, že vždy odvozuje jednoduchý typ <xref:System.String>jako.  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 Odvodí datový typ silného typu. Vyvolá výjimku, pokud se používá s <xref:System.Data.DataTable>.  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 Ignoruje všechna vložená schémata a čte data do <xref:System.Data.DataSet> stávajícího schématu.  
  
## <a name="attributes"></a>Atributy  
 Jak je definováno v [tabulkách odvození](inferring-tables.md), element s atributy bude odvozen jako tabulka. Atributy daného prvku budou následně odvozeny jako sloupce pro tabulku. Vlastnost **ColumnMapping** sloupců bude nastavena na **MappingType. Attribute**, aby bylo zajištěno, že názvy sloupců budou zapsány jako atributy, pokud je schéma zapsáno zpět do formátu XML. Hodnoty atributů jsou uloženy v řádku tabulky. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci, **attr1** a **attr2**. Vlastnost **ColumnMapping** obou sloupců bude nastavena na **MappingType. Attribute**.  
  
 **Integrován** DocumentElement  
  
 **Stolní** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|Hodnota1|Argument|  
  
## <a name="elements-without-attributes-or-child-elements"></a>Prvky bez atributů nebo podřízených elementů  
 Pokud element nemá žádné podřízené elementy nebo atributy, bude odvozen jako sloupec. Vlastnost **ColumnMapping** sloupce bude nastavena na **MappingType. element**. Text podřízených elementů je uložený v řádku v tabulce. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci, **ChildElement1** a **ChildElement2**. Vlastnost **ColumnMapping** obou sloupců bude nastavena na **MappingType. element**.  
  
 **Integrován** DocumentElement  
  
 **Stolní** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## <a name="see-also"></a>Viz také:

- [Odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md)
- [Načtení datové sady z XML](loading-a-dataset-from-xml.md)
- [Načtení informací o schématu datové sady z XML](loading-dataset-schema-information-from-xml.md)
- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
