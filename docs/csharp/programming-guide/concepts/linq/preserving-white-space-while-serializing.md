---
title: Zachování mezer při Serializing3
description: Naučte se ovládat prázdné znaky při serializaci stromu XML pomocí metod v třídách XElement a XDocument.
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 01e68671e2fde1a2b5b1d0bc429841077ba0205f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303410"
---
# <a name="preserving-white-space-while-serializing"></a>Zachování prázdných znaků při serializaci
Toto téma popisuje, jak ovládat prázdné znaky při serializaci stromu XML.  
  
 Běžným scénářem je čtení odsazeného XML, vytvoření stromu XML ve formátu paměti bez prázdných textových uzlů (tj. Neuchování prázdných znaků), provedení některých operací v XML a následné uložení XML s odsazením. Při serializaci XML s formátováním je zachováno pouze významné prázdné znaky ve stromu XML. Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Dalším běžným scénářem je číst a upravovat kód XML, který již byl záměrně odsazen. Toto odsazení nebudete chtít nijak měnit. Chcete-li to provést v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , zachováte prázdné místo při načítání nebo analýze XML a při serializaci kódu XML zakážete formátování.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Chování metod, které serializovat stromy XML, v prázdném prostoru  
 Následující metody v <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> třídách a SERIALIZOVAT strom XML. Strom XML lze serializovat do souboru, <xref:System.IO.TextReader> nebo <xref:System.Xml.XmlReader> . `ToString`Metoda je serializována do řetězce.  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement. ToString ()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument. ToString ()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 Pokud metoda nepřijímá <xref:System.Xml.Linq.SaveOptions> jako argument, pak metoda naformátuje (odsadí) serializovaný kód XML. V tomto případě je zahozeno veškeré nevýznamné prázdné znaky ve stromu XML.  
  
 Pokud metoda převezme <xref:System.Xml.Linq.SaveOptions> jako argument, můžete určit, že metoda nebude formátovat (odsazovat) serializovaného XML. V tomto případě je zachováno veškeré prázdné znaky ve stromu XML.  
