---
title: Kroky v procesu serializace
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: ef81ecc7ca177fa9360f53a6b66015412d282065
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084909"
---
# <a name="steps-in-the-serialization-process"></a>Kroky v procesu serializace
Když <xref:System.Runtime.Serialization.Formatter.Serialize*> metoda je volána na [formátovací modul](xref:System.Runtime.Serialization.Formatter), serializaci objektů pokračuje podle následujícího pořadí pravidel:

- Chcete-li zjistit, zda formátovací modul obsahuje náhradní selektor se provede kontrola. Pokud formátovací modul, zkontrolujte, zda selektor náhradní zpracovává objekty daného typu. Pokud selektor zpracovává typ objektu <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> je volán na náhradní selektor.

- Pokud není k dispozici žádné náhradní selektor nebo pokud nezpracovává typ objektu, chcete-li určit, zda je označeno objekt se provede kontrola [Serializable](xref:System.SerializableAttribute) atribut. Pokud ne, je objekt <xref:System.Runtime.Serialization.SerializationException> je vyvolána výjimka.

- Pokud objekt označen odpovídajícím způsobem, zkontrolujte, zda daný objekt implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní. Pokud je objekt, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> je volána v objektu.
  
- Pokud objekt neimplementuje <xref:System.Runtime.Serialization.ISerializable>, se používá výchozí zásady serializace, serializaci všechna pole nejsou označeny jako [NonSerialized](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Viz také:

- [Binární serializace](binary-serialization.md)  
- [Serializace XML a SOAP](xml-and-soap-serialization.md)
