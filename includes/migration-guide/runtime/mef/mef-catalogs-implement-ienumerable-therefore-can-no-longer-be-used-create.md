---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803729"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Katalogy MEF implementují rozhraní IEnumerable a proto již lze vytvořit serializátor

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, katalogy MEF implementovat rozhraní IEnumerable a proto již lze vytvořit serializátor (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> objekt). Při pokusu o serializaci katalogu MEF vyvolá výjimku.|
|Doporučení|MEF lze vytvořit serializátor již nebudete používat|
|Rozsah|Hlavní|
|Version|4.5|
|Type|Modul runtime|
