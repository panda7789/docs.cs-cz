---
title: Kroky v procesu serializace
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2709af8e63428db2165ecd1256bce4f6690ae0a6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="steps-in-the-serialization-process"></a>Kroky v procesu serializace
Když <xref:System.Runtime.Serialization.Formatter.Serialize*> metoda je volána v [formátovací modul](xref:System.Runtime.Serialization.Formatter), serializace objektu pokračuje podle pořadí následující pravidla:

- Chcete-li zjistit, zda formátovací modul obsahuje náhradní selektor se provede kontrola. Pokud formátovací modul, zkontrolujte, zda selektor náhradní zpracovává objekty daného typu. Pokud selektor zpracovává typ objektu, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> se volá na náhradní selektor.

- Pokud neexistuje žádný výběr náhradní nebo pokud nezpracovává typ objektu, ověření k určení, zda je označené jako objekt [Serializable](xref:System.SerializableAttribute) atribut. Pokud není objekt, <xref:System.Runtime.Serialization.SerializationException> je vyvolána výjimka.

- Pokud objekt je označena odpovídajícím způsobem, zkontrolujte, zda objekt implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní. Pokud je objekt, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> je volána v objektu.
  
- Pokud objekt neimplementuje <xref:System.Runtime.Serialization.ISerializable>, se používá výchozí zásady serializace, serializaci všechna pole nesmí být označený jako [NonSerialized](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Viz také  
 [Binární serializace](binary-serialization.md)  
 [XML a serializace protokolu SOAP](xml-and-soap-serialization.md)