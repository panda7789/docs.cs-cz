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
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="34e78-102">Kroky v procesu serializace</span><span class="sxs-lookup"><span data-stu-id="34e78-102">Steps in the serialization process</span></span>
<span data-ttu-id="34e78-103">Pokud je <xref:System.Runtime.Serialization.Formatter.Serialize%2A> metoda volána pro [formátovací modul](xref:System.Runtime.Serialization.Formatter), serializace objektu pokračuje podle následujícího pořadí pravidel:</span><span class="sxs-lookup"><span data-stu-id="34e78-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="34e78-104">Chcete-li zjistit, zda formátovací modul obsahuje náhradní selektor se provede kontrola.</span><span class="sxs-lookup"><span data-stu-id="34e78-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="34e78-105">Pokud formátovací modul, zkontrolujte, zda selektor náhradní zpracovává objekty daného typu.</span><span class="sxs-lookup"><span data-stu-id="34e78-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="34e78-106">Pokud selektor zpracovává typ objektu, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> je volána v selektoru náhradních položek.</span><span class="sxs-lookup"><span data-stu-id="34e78-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="34e78-107">Pokud není k dispozici žádný náhradní selektor nebo pokud nezpracovává typ objektu, je provedena kontroly pro určení, zda je objekt označen atributem [serializovatelný](xref:System.SerializableAttribute) .</span><span class="sxs-lookup"><span data-stu-id="34e78-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="34e78-108">Pokud objekt není, <xref:System.Runtime.Serialization.SerializationException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="34e78-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="34e78-109">Je-li objekt označen příznakem odpovídajícím způsobem, ověřte <xref:System.Runtime.Serialization.ISerializable> , zda objekt implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="34e78-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="34e78-110">Pokud objekt je, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> je volána na objektu.</span><span class="sxs-lookup"><span data-stu-id="34e78-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> is called on the object.</span></span>
  
- <span data-ttu-id="34e78-111">Pokud objekt neimplementuje <xref:System.Runtime.Serialization.ISerializable>, použije se výchozí zásada serializace a serializace všech polí, která nejsou označena jako [neserializovatelné](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="34e78-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="34e78-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="34e78-112">See also</span></span>

- [<span data-ttu-id="34e78-113">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="34e78-113">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="34e78-114">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="34e78-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
