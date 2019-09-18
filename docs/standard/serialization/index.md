---
title: Serializace – .NET
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: e6db24326c79ab6509b253c45c27f87a2aacd73c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053351"
---
# <a name="serialization-in-net"></a>Serializace v .NET

Serializace je proces převodu stav objektu do tvaru, který může být zachována nebo přenosu. Doplňkovým serializace je deserializace, která převádí na objekt datového proudu. Tyto procesy společně umožňují ukládání a přenos dat.  
  
Rozhraní .NET nabízí tyto technologie serializace:  
  
- [Binární serializace](binary-serialization.md) zachovává věrnost typu, což je užitečné pro zachování stavu objektu mezi různými voláními aplikace. Například můžete sdílet objekt mezi různými aplikacemi pomocí jeho serializace do schránky. Může serializovat objekt do datového proudu, na disk do paměti, v síti a tak dále. Vzdálená komunikace používá serializace k předání objekty "hodnotou" z jedné domény počítače nebo aplikace do jiného.  
  
- [Serializace XML a SOAP](xml-and-soap-serialization.md) serializovat pouze veřejné vlastnosti a pole a nezachovává věrnost typu. To je užitečné, pokud chcete zadat nebo spotřebovat data bez omezení aplikace, která používá data. Protože kód XML je otevřený standard, je to atraktivní volba pro sdílení dat v rámci webu. Protokol SOAP je rovněž otevřený standard, díky čemuž je atraktivní výběru.  
  
- [Serializace JSON](system-text-json-overview.md) pouze veřejné vlastnosti a nezachovává věrnost typu. JSON je otevřený standard, který je atraktivní volbou pro sdílení dat na celém webu.

## <a name="reference"></a>Reference

<xref:System.Runtime.Serialization>  
Obsahuje třídy, které lze použít pro serializaci a deserializaci objektů.
  
<xref:System.Xml.Serialization>  
Obsahuje třídy, které lze použít k serializaci objektů do formátu dokumentů XML nebo datových proudů.

<xref:System.Text.Json>  
Obsahuje třídy, které lze použít k serializaci objektů do dokumentů formátu JSON nebo datových proudů.
