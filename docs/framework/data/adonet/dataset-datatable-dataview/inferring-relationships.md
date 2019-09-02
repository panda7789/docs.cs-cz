---
title: Odvozování relací
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 92a4953dc7f5119ffbf171ff2a7bf5b58e896638
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204768"
---
# <a name="inferring-relationships"></a>Odvozování relací
Pokud prvek, který je odvozen jako tabulka, má podřízený element, který je také odvozen jako tabulka, <xref:System.Data.DataRelation> vytvoří se mezi těmito dvěma tabulkami. Nový sloupec s názvem **ParentTableName_Id** se přidá do tabulky vytvořené pro nadřazený element a vytvoří se tabulka vytvořená pro podřízený element. Vlastnost **ColumnMapping** tohoto sloupce identity bude nastavena na **MappingType. Hidden**. Sloupec bude automaticky zvyšovat primární klíč pro nadřazenou tabulku a bude použit pro **relaci DataRelation** mezi oběma tabulkami. Datový typ sloupce přidáno identity bude **System. Int32**, na rozdíl od datového typu všech ostatních odvozených sloupců, což je **System. String**. A <xref:System.Data.ForeignKeyConstraint> s **DeleteRule** = **Cascade** se vytvoří také pomocí nového sloupce v nadřazené i podřízené tabulce.  
  
 Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří dvě tabulky: **Element1** a **ChildElement1**.  
  
 Tabulka **Element1** bude mít dva sloupce: **Element1_Id** a **ChildElement2**. Vlastnost **ColumnMapping** sloupce **Element1_Id** bude nastavena na **MappingType. Hidden**. Vlastnost **ColumnMapping** sloupce **ChildElement2** bude nastavena na **MappingType. element**. Sloupec **Element1_Id** se nastaví jako primární klíč tabulky **Element1** .  
  
 Tabulka **ChildElement1** bude mít tři sloupce: **attr1**, **attr2** a **Element1_Id**. Vlastnost **ColumnMapping** pro sloupce **attr1** a **attr2** se nastaví na **MappingType. Attribute**. Vlastnost **ColumnMapping** sloupce **Element1_Id** bude nastavena na **MappingType. Hidden**.  
  
 **DataRelation** a **Objekt ForeignKeyConstraint** se vytvoří pomocí sloupců **Element1_Id** z obou tabulek.  
  
 **Integrován** DocumentElement  
  
 **Stolní** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **Stolní** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|Hodnota1|Argument|0|  
  
 **DataRelation** Element1_ChildElement1  
  
 **Nadřazená tabulka:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **Podřízená tabulka:** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **Vnořen** Pravda  
  
 **Objekt ForeignKeyConstraint** Element1_ChildElement1  
  
 **Kolo** Element1_Id  
  
 **Nadřazená tabulka:** Element1  
  
 **Podřízená tabulka:** ChildElement1  
  
 **DeleteRule:** Nášejí  
  
 **AcceptRejectRule:** Žádné  
  
## <a name="see-also"></a>Viz také:

- [Odvození relační struktury datové sady z XML](inferring-dataset-relational-structure-from-xml.md)
- [Načtení datové sady z XML](loading-a-dataset-from-xml.md)
- [Načtení informací o schématu datové sady z XML](loading-dataset-schema-information-from-xml.md)
- [Vnoření datových relací](nesting-datarelations.md)
- [Použití XML v datové sadě](using-xml-in-a-dataset.md)
- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
