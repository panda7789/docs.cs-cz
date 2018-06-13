---
title: Kroky v procesu serializace
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: b44b3b0539237c0f0d0a4af877e8955c6f612003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581817"
---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="2494f-102">Kroky v procesu serializace</span><span class="sxs-lookup"><span data-stu-id="2494f-102">Steps in the serialization process</span></span>
<span data-ttu-id="2494f-103">Když <xref:System.Runtime.Serialization.Formatter.Serialize*> metoda je volána v [formátovací modul](xref:System.Runtime.Serialization.Formatter), serializace objektu pokračuje podle pořadí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="2494f-103">When the <xref:System.Runtime.Serialization.Formatter.Serialize*> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="2494f-104">Chcete-li zjistit, zda formátovací modul obsahuje náhradní selektor se provede kontrola.</span><span class="sxs-lookup"><span data-stu-id="2494f-104">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="2494f-105">Pokud formátovací modul, zkontrolujte, zda selektor náhradní zpracovává objekty daného typu.</span><span class="sxs-lookup"><span data-stu-id="2494f-105">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="2494f-106">Pokud selektor zpracovává typ objektu, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> se volá na náhradní selektor.</span><span class="sxs-lookup"><span data-stu-id="2494f-106">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="2494f-107">Pokud neexistuje žádný výběr náhradní nebo pokud nezpracovává typ objektu, ověření k určení, zda je označené jako objekt [Serializable](xref:System.SerializableAttribute) atribut.</span><span class="sxs-lookup"><span data-stu-id="2494f-107">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="2494f-108">Pokud není objekt, <xref:System.Runtime.Serialization.SerializationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2494f-108">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="2494f-109">Pokud objekt je označena odpovídajícím způsobem, zkontrolujte, zda objekt implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2494f-109">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="2494f-110">Pokud je objekt, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> je volána v objektu.</span><span class="sxs-lookup"><span data-stu-id="2494f-110">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> is called on the object.</span></span>
  
- <span data-ttu-id="2494f-111">Pokud objekt neimplementuje <xref:System.Runtime.Serialization.ISerializable>, se používá výchozí zásady serializace, serializaci všechna pole nesmí být označený jako [NonSerialized](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="2494f-111">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="2494f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2494f-112">See Also</span></span>  
 [<span data-ttu-id="2494f-113">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="2494f-113">Binary Serialization</span></span>](binary-serialization.md)  
 [<span data-ttu-id="2494f-114">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="2494f-114">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)