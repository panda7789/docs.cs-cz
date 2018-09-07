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
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="93078-102">Kroky v procesu serializace</span><span class="sxs-lookup"><span data-stu-id="93078-102">Steps in the serialization process</span></span>
<span data-ttu-id="93078-103">Když <xref:System.Runtime.Serialization.Formatter.Serialize*> metoda je volána na [formátovací modul](xref:System.Runtime.Serialization.Formatter), serializaci objektů pokračuje podle následujícího pořadí pravidel:</span><span class="sxs-lookup"><span data-stu-id="93078-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize*> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="93078-104">Chcete-li zjistit, zda formátovací modul obsahuje náhradní selektor se provede kontrola.</span><span class="sxs-lookup"><span data-stu-id="93078-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="93078-105">Pokud formátovací modul, zkontrolujte, zda selektor náhradní zpracovává objekty daného typu.</span><span class="sxs-lookup"><span data-stu-id="93078-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="93078-106">Pokud selektor zpracovává typ objektu <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> je volán na náhradní selektor.</span><span class="sxs-lookup"><span data-stu-id="93078-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="93078-107">Pokud není k dispozici žádné náhradní selektor nebo pokud nezpracovává typ objektu, chcete-li určit, zda je označeno objekt se provede kontrola [Serializable](xref:System.SerializableAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="93078-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="93078-108">Pokud ne, je objekt <xref:System.Runtime.Serialization.SerializationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="93078-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="93078-109">Pokud objekt označen odpovídajícím způsobem, zkontrolujte, zda daný objekt implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="93078-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="93078-110">Pokud je objekt, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> je volána v objektu.</span><span class="sxs-lookup"><span data-stu-id="93078-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> is called on the object.</span></span>
  
- <span data-ttu-id="93078-111">Pokud objekt neimplementuje <xref:System.Runtime.Serialization.ISerializable>, se používá výchozí zásady serializace, serializaci všechna pole nejsou označeny jako [NonSerialized](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="93078-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="93078-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93078-112">See also</span></span>

- [<span data-ttu-id="93078-113">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="93078-113">Binary Serialization</span></span>](binary-serialization.md)  
- [<span data-ttu-id="93078-114">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="93078-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
