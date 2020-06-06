---
title: Kroky v procesu serializace
description: Proces serializace začíná při volání metody serializace pro formátovací modul. Tento článek popisuje posloupnost událostí.
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: 1f749b9102182e78bc3fda436cf386a9f5759d5a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "83379104"
---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="0390a-104">Kroky v procesu serializace</span><span class="sxs-lookup"><span data-stu-id="0390a-104">Steps in the serialization process</span></span>
<span data-ttu-id="0390a-105">Pokud <xref:System.Runtime.Serialization.Formatter.Serialize%2A> je metoda volána pro [formátovací modul](xref:System.Runtime.Serialization.Formatter), serializace objektu pokračuje podle následujícího pořadí pravidel:</span><span class="sxs-lookup"><span data-stu-id="0390a-105">When the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="0390a-106">Chcete-li zjistit, zda formátovací modul obsahuje náhradní selektor se provede kontrola.</span><span class="sxs-lookup"><span data-stu-id="0390a-106">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="0390a-107">Pokud formátovací modul, zkontrolujte, zda selektor náhradní zpracovává objekty daného typu.</span><span class="sxs-lookup"><span data-stu-id="0390a-107">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="0390a-108">Pokud selektor zpracovává typ objektu, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> je volána v selektoru náhradních položek.</span><span class="sxs-lookup"><span data-stu-id="0390a-108">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="0390a-109">Pokud není k dispozici žádný náhradní selektor nebo pokud nezpracovává typ objektu, je provedena kontroly pro určení, zda je objekt označen atributem [serializovatelný](xref:System.SerializableAttribute) .</span><span class="sxs-lookup"><span data-stu-id="0390a-109">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="0390a-110">Pokud objekt není, <xref:System.Runtime.Serialization.SerializationException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="0390a-110">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="0390a-111">Je-li objekt označen příznakem odpovídajícím způsobem, ověřte, zda objekt implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0390a-111">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="0390a-112">Pokud objekt <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> je, je volána na objektu.</span><span class="sxs-lookup"><span data-stu-id="0390a-112">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> is called on the object.</span></span>
  
- <span data-ttu-id="0390a-113">Pokud objekt neimplementuje <xref:System.Runtime.Serialization.ISerializable> , použije se výchozí zásada serializace a serializace všech polí, která nejsou označena jako [neserializovatelné](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="0390a-113">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="0390a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="0390a-114">See also</span></span>

- [<span data-ttu-id="0390a-115">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="0390a-115">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="0390a-116">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="0390a-116">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
