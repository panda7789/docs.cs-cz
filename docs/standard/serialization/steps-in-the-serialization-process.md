---
title: Kroky v procesu serializace
description: Proces serializace začíná při volání metody serializace pro formátovací modul. Tento článek popisuje posloupnost událostí.
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: 1f749b9102182e78bc3fda436cf386a9f5759d5a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379104"
---
# <a name="steps-in-the-serialization-process"></a>Kroky v procesu serializace
Pokud <xref:System.Runtime.Serialization.Formatter.Serialize%2A> je metoda volána pro [formátovací modul](xref:System.Runtime.Serialization.Formatter), serializace objektu pokračuje podle následujícího pořadí pravidel:

- Chcete-li zjistit, zda formátovací modul obsahuje náhradní selektor se provede kontrola. Pokud formátovací modul, zkontrolujte, zda selektor náhradní zpracovává objekty daného typu. Pokud selektor zpracovává typ objektu, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> je volána v selektoru náhradních položek.

- Pokud není k dispozici žádný náhradní selektor nebo pokud nezpracovává typ objektu, je provedena kontroly pro určení, zda je objekt označen atributem [serializovatelný](xref:System.SerializableAttribute) . Pokud objekt není, <xref:System.Runtime.Serialization.SerializationException> je vyvolána.

- Je-li objekt označen příznakem odpovídajícím způsobem, ověřte, zda objekt implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní. Pokud objekt <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> je, je volána na objektu.
  
- Pokud objekt neimplementuje <xref:System.Runtime.Serialization.ISerializable> , použije se výchozí zásada serializace a serializace všech polí, která nejsou označena jako [neserializovatelné](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Viz také

- [Binární serializace](binary-serialization.md)
- [Serializace XML a SOAP](xml-and-soap-serialization.md)
