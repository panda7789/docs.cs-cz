---
title: Zachování prázdných znaků při načítání nebo analýze XML
description: Naučte se ovládat chování při načítání nebo analýze XML, konkrétně chování metod, které naplňují stromy XML.
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: 3c044937d38f9f89ebc114af3eddbf5116c392ad
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302838"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>Zachování prázdných znaků při načítání nebo analýze XML
Toto téma popisuje, jak ovládat chování prázdného místa v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Běžným scénářem je čtení odsazeného XML, vytvoření stromu XML v paměti bez jakýchkoli textových uzlů s prázdnými znaky (tj. bez zachovávání prázdných znaků), provedení některých operací v XML a následné uložení XML s odsazením. Při serializaci XML s formátováním je zachováno pouze významné prázdné znaky ve stromu XML. Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Dalším běžným scénářem je číst a upravovat kód XML, který již byl záměrně odsazen. Toto odsazení nebudete chtít nijak měnit. Chcete-li to provést v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , zachováte prázdné místo při načítání nebo analýze XML a při serializaci kódu XML zakážete formátování.  
  
 Toto téma popisuje prázdné místo v případě metod, které naplňují stromy XML. Informace o řízení prázdných znaků při serializaci stromů XML naleznete v tématu [zachování mezer při serializaci](./preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>Chování metod, které naplňují stromy XML  
 Následující metody v <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> třídách a naplní strom XML. Můžete naplnit strom XML ze souboru, a <xref:System.IO.TextReader> , <xref:System.Xml.XmlReader> nebo pomocí řetězce:  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Pokud metoda nepřijímá <xref:System.Xml.Linq.LoadOptions> jako argument, nezachová metoda nevýznamné prázdné znaky.  
  
 Ve většině případů, pokud metoda přebírá <xref:System.Xml.Linq.LoadOptions> jako argument, můžete volitelně zachovat nevýznamné prázdné znaky jako textové uzly ve stromu XML. Nicméně pokud metoda načítá XML z <xref:System.Xml.XmlReader> a, pak <xref:System.Xml.XmlReader> Určuje, zda bude prázdný znak zachován nebo ne. Nastavení <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> nebude mít žádný vliv.  
  
 S těmito metodami, pokud je zachováno prázdné místo, je do stromu XML jako uzly vloženo nevýznamné prázdné znaky <xref:System.Xml.Linq.XText> . Pokud prázdné znaky nejsou zachovány, textové uzly nejsou vloženy.  
  
 Strom XML lze vytvořit pomocí <xref:System.Xml.XmlWriter> . Uzly, které jsou zapsány do, <xref:System.Xml.XmlWriter> jsou vyplněny ve stromové struktuře. Při sestavování stromu XML pomocí této metody však jsou zachovány všechny uzly bez ohledu na to, zda je uzel prázdný znak nebo není nebo zda je mezera významná.  
  