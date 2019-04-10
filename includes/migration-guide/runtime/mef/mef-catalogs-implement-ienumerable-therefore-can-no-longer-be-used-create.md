---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235287"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Katalogy MEF implementují rozhraní IEnumerable a proto již lze vytvořit serializátor

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, katalogy MEF implementovat rozhraní IEnumerable a proto již lze vytvořit serializátor (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> objekt). Při pokusu o serializaci katalogu MEF vyvolá výjimku.|
|Doporučení|MEF lze vytvořit serializátor již nebudete používat|
|Rozsah|Hlavní|
|Version|4.5|
|Type|Modul runtime|
