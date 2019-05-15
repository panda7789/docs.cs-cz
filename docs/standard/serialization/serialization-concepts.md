---
title: Koncepty serializace
ms.date: 08/07/2017
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
ms.openlocfilehash: 99716a6346689ac4d3201f83b0b8204cad462e8e
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593333"
---
# <a name="serialization-concepts"></a>Koncepty serializace
Proč byste se měli použít serializaci? Dva nejdůležitější důvody jsou k uchování stav objektu do úložiště média, takže přesná kopie může být později znovu vytvořena a posílat objektu podle hodnoty od jeden aplikační domény do druhé. Můžete například serializace slouží k uložení stavu relace technologie ASP.NET a objekty zkopírovat do schránky ve Windows Forms. Také se používá ve vzdálené komunikace předat objekty podle hodnoty z domény jednu aplikaci do jiného.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a>Trvalé úložiště
Často je nezbytné k uložení hodnoty polí objektu na disk a potom později načíst tato data. Přestože je to snadné dosáhnout bez ohledu na serializace, tento přístup je často náročný a chyby k chybám a změní postupně složitější, pokud je třeba sledovat hierarchie objektů. Představte si aplikaci velké firmy, která obsahuje tisíce objekty, zápisu a nutnosti psaní kódu pro uložení a obnovení polí a vlastností, z disku a disk pro každý objekt. Serializace poskytuje vhodný mechanismus pro dosažení tohoto cíle.

Modul common language runtime spravuje, jak jsou objekty uložené v paměti a poskytuje mechanismus pro automatické serializace pomocí [reflexe](../../../docs/framework/reflection-and-codedom/reflection.md). Pokud je objekt serializován, název třídy, sestavení a datových členů instance třídy jsou zapsány do úložiště. Objekty často ukládat odkazy na další instance proměnné členů. Při serializován třídu pro Serializační stroj sleduje odkazované objekty, již serializován, chcete-li zajistit, že na stejný objekt nelze serializovat, více než jednou. Architektura serializace zadaná pomocí rozhraní .NET Framework správně zpracovává grafy a objektů cyklické odkazy automaticky. Jediným požadavkem umístí na objekt, grafy je, že všechny objekty, odkazuje serializovaný objekt musí být také označen jako `Serializable` (Další informace najdete v tématu [základní serializace](basic-serialization.md)). Pokud není to, bude vyvolána výjimka, když serializátor pokusí serializaci zrušeno označení objektu.

Když je deserializovat serializovaná třídy, se znovu vytvoří třídu a hodnoty datových členů jsou automaticky obnoví.

## <a name="marshal-by-value"></a>Zařazování podle hodnoty
Objekty jsou platné pouze v doméně aplikace, kde jsou vytvořeny. Jakýkoliv pokus o předání objektu jako parametr nebo je vrátit v důsledku se nezdaří, pokud objekt je odvozen z `MarshalByRefObject` nebo je označeno jako `Serializable`. Pokud objekt je označen jako `Serializable`, objekt bude automaticky serializován, přenášet od jeden aplikační domény na druhý a potom deserializovat k vytvoření přesnou kopii objektu v druhém doménu aplikace. Tento proces je obvykle označován jako zařazování podle hodnot.
 
Pokud objekt je odvozen od `MarshalByRefObject`, odkaz na objekt je předán z jednoho aplikační domény na jiný, nikoli samotného objektu. Můžete také označit objekt, který je odvozen od `MarshalByRefObject` jako `Serializable`. Když tento objekt se používá u vzdálené komunikace zodpovědná za serializaci, které jsou předem nakonfigurované s náhradní selektor formátování (`SurrogateSelector`), přebírá řízení procesu serializace a nahradí všechny objekty, které jsou odvozeny z `MarshalByRefObject` s proxy server. Bez `SurrogateSelector` na místě, architektura serializace následuje standardní serializace pravidel popsaných v [kroky v procesu serializace](steps-in-the-serialization-process.md).  

## <a name="related-sections"></a>Související oddíly  
 [Binární serializace](../../../docs/standard/serialization/binary-serialization.md)  
 Popisuje binární serializace mechanismus, který je součástí common language runtime.  
  
 [Vzdálené komunikace .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))\
 Popisuje různé komunikační metody k dispozici v rozhraní .NET Framework pro vzdálenou komunikaci.  
  
 [Serializace XML a SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Popisuje mechanismus serializace XML a SOAP, která je součástí common language runtime.
