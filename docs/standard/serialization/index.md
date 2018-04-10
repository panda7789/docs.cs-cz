---
title: Serializace v .NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1a0d9f5fd32b5610e3d7b05455c7bd3c55b5b77e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="serialization-in-net"></a>Serializace v .NET
Serializace je proces převodu stav objektu do tvaru, který může být zachována nebo přenosu. Doplňkovým serializace je deserializace, která převádí na objekt datového proudu. Tyto procesy dohromady, povolit, aby snadno ukládat a přenesených údaje.  
  
Služeb .NET features dvě technologie serializace:  
  
-   Binární serializace zachová věrnost typu, což je užitečné pro zachování stav objektu mezi různé volání aplikace. Například můžete sdílet objekt mezi různými aplikacemi pomocí jeho serializace do schránky. Může serializovat objekt do datového proudu, na disk do paměti, v síti a tak dále. Vzdálená komunikace používá serializace k předání objekty "hodnotou" z jedné domény počítače nebo aplikace do jiného.  
  
-   Serializace XML serializuje pouze veřejné vlastnosti a pole a nezachovává věrnost typu. To je užitečné, pokud chcete zadat nebo spotřebovat data bez omezení aplikace, která používá data. Protože kód XML je otevřený standard, je to atraktivní volba pro sdílení dat v rámci webu. Protokol SOAP je rovněž otevřený standard, díky čemuž je atraktivní výběru.  
  
## <a name="in-this-section"></a>V tomto oddílu  
[Postupy: Serializace](../../../docs/standard/serialization/serialization-how-to-topics.md)  
Obsahuje seznam odkazů na témata s postupy, které jsou obsažené v této části.
  
[Binární serializace](../../../docs/standard/serialization/binary-serialization.md)  
Popisuje binární serializace mechanismus, který je součástí common language runtime.

[Serializace XML a SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
Popisuje mechanismus serializace XML a SOAP, která je součástí common language runtime.

[Nástroje pro serializaci](../../../docs/standard/serialization/serialization-tools.md)  
Tyto nástroje pomáhají při vývoji serializace kódu.

[Ukázky serializace](../../../docs/standard/serialization/serialization-samples.md)  
Ukázky ukazují, jak provést serializace.

## <a name="reference"></a>Odkaz
<xref:System.Runtime.Serialization>Obsahuje třídy, které lze použít pro serializaci a deserializaci objektů.
  
<xref:System.Xml.Serialization>  
Obsahuje třídy, které lze použít k serializaci objektů do formátu dokumentů XML nebo datových proudů.