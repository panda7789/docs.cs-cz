---
title: Koncepty serializace
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1f442f450aea5833fd21e57980c842cc1559ccc1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="serialization-concepts"></a>Koncepty serializace
Proč byste se měli použít serializaci? Dva nejdůležitější důvody jsou k uchování stav objektu do úložiště média, takže přesná kopie může být později znovu vytvořena a posílat objektu podle hodnoty od jeden aplikační domény do druhé. Můžete například serializace slouží k uložení stavu relace technologie ASP.NET a objekty zkopírovat do schránky ve Windows Forms. Také se používá ve vzdálené komunikace předat objekty podle hodnoty z domény jednu aplikaci do jiného.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a>Trvalé úložiště
Často je nezbytné k uložení hodnoty polí objektu na disk a potom později načíst tato data. Přestože je to snadné dosáhnout bez ohledu na serializace, tento přístup je často náročný a chyby k chybám a změní postupně složitější, pokud je třeba sledovat hierarchie objektů. Představte si aplikaci velké firmy, která obsahuje tisíce objekty, zápisu a nutnosti psaní kódu pro uložení a obnovení polí a vlastností, z disku a disk pro každý objekt. Serializace poskytuje vhodný mechanismus pro dosažení tohoto cíle.

Modul common language runtime spravuje, jak jsou objekty uložené v paměti a poskytuje mechanismus serializace automatizované pomocí [reflexe](../../../docs/framework/reflection-and-codedom/reflection.md). Pokud je objekt serializován, název třídy, sestavení a datových členů instance třídy jsou zapsány do úložiště. Objekty často ukládat odkazy na další instance proměnné členů. Při serializován třídu pro Serializační stroj sleduje odkazované objekty, již serializován, chcete-li zajistit, že na stejný objekt nelze serializovat, více než jednou. Architektura serializace opatřeného [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] správně zpracovává grafy a objektů cyklické odkazy automaticky. Umístit do objektu grafy Jediným požadavkem je, že všechny objekty, které se odkazuje serializovaný objekt musí být také označen jako `Serializable` (Další informace najdete v tématu [základní serializace](basic-serialization.md)). Pokud není to, bude vyvolána výjimka, když serializátor pokusí serializaci zrušeno označení objektu.

Když serializovaných třída deserializován, třídy se znovu vytvoří a jsou automaticky obnovit hodnoty datových členů.

## <a name="marshal-by-value"></a>Zařazování podle hodnoty
Objekty jsou platné pouze v doméně aplikace, kde jsou vytvořeny. Pokusy o tento objekt předat jako parametr, nebo může vracet se v důsledku se nezdaří, pokud objekt je odvozena z `MarshalByRefObject` nebo je označena jako `Serializable`. Pokud objekt je označen jako `Serializable`, automaticky použije objekt serializován, přenášet z domény jednu aplikaci na druhý a poté deserializován k vytvoření přesnou kopii objektu v druhé doméně aplikace. Tento proces je obvykle označován jako zařazování podle hodnot.
 
Když je objekt odvozena z `MarshalByRefObject`, odkaz na objekt předaný z domény jedné aplikace do jiného, než samotného objektu. Můžete také označit objekt, který je odvozen od `MarshalByRefObject` jako `Serializable`. Když tento objekt se používá s vzdálenou komunikaci, zodpovědná za serializace, který byl předem nakonfigurován s náhradní selektor formátování (`SurrogateSelector`), přebírá řízení serializace procesu a nahradí všechny objekty, které jsou odvozené z `MarshalByRefObject` s proxy server. Bez `SurrogateSelector` na místě, odpovídá architektuře serializace standardní serializace pravidel popsaných v [kroků v procesu serializace](steps-in-the-serialization-process.md).  

## <a name="related-sections"></a>Související oddíly  
 [Binární serializace](../../../docs/standard/serialization/binary-serialization.md)  
 Popisuje binární serializace mechanismus, který je součástí common language runtime.  
  
 [Vzdálených objektů](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 Popisuje různé komunikační metody k dispozici v rozhraní .NET Framework pro vzdálenou komunikaci.  
  
 [XML a serializace protokolu SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Popisuje mechanismus serializace XML a SOAP, která je součástí common language runtime.
