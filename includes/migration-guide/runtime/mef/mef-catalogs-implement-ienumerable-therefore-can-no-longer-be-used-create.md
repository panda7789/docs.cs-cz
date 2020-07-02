---
ms.openlocfilehash: 598df2121b480d411dac9c5571772a4a8d22b5ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620035"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Katalogy MEF implementují rozhraní IEnumerable a proto se už nedají použít k vytvoření serializátoru.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,5, katalogy MEF implementují rozhraní IEnumerable, a proto je nelze nadále používat k vytvoření serializátoru ( <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> objektu). Při pokusu o serializaci katalogu MEF vyvolá výjimku.

#### <a name="suggestion"></a>Návrh

Rozhraní MEF již nelze použít k vytvoření serializátoru.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Hlavní|
|Verze|4.5|
|Typ|Modul runtime|
