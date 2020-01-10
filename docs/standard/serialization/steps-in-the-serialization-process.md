---
title: Kroky v procesu serializace
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: f30dd550437e6bc1030c79865bf2edd2c0efbfa9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741047"
---
# <a name="steps-in-the-serialization-process"></a>Kroky v procesu serializace
Když je metoda <xref:System.Runtime.Serialization.Formatter.Serialize%2A> volána pro [formátovací modul](xref:System.Runtime.Serialization.Formatter), serializace objektu pokračuje podle následujícího pořadí pravidel:

- Chcete-li zjistit, zda formátovací modul obsahuje náhradní selektor se provede kontrola. Pokud formátovací modul, zkontrolujte, zda selektor náhradní zpracovává objekty daného typu. Pokud selektor zpracovává typ objektu, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> je volána v náhradním selektoru.

- Pokud není k dispozici žádný náhradní selektor nebo pokud nezpracovává typ objektu, je provedena kontroly pro určení, zda je objekt označen atributem [serializovatelný](xref:System.SerializableAttribute) . Pokud objekt není, je vyvolána <xref:System.Runtime.Serialization.SerializationException>.

- Pokud je objekt vhodně označený, ověřte, zda objekt implementuje rozhraní <xref:System.Runtime.Serialization.ISerializable>. Pokud objekt je, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> je volána na objektu.
  
- Pokud objekt neimplementuje <xref:System.Runtime.Serialization.ISerializable>, použije se výchozí zásada serializace a serializace všech polí, která nejsou označena jako [neserializovatelné](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Viz také:

- [Binární serializace](binary-serialization.md)
- [Serializace XML a SOAP](xml-and-soap-serialization.md)
