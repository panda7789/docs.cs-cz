---
title: Jak zjistit, zda je objekt .NET Standard serializovat
description: Ukazuje, jak určit, zda lze typu .NET Standard serializovat v době běhu.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 196e99ab1f1a0baae53c6a1dc295b135e36fbfe0
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324591"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="7dc12-103">Jak zjistit, zda je objekt .NET Standard serializovat</span><span class="sxs-lookup"><span data-stu-id="7dc12-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="7dc12-104">.NET Standard je specifikace, která definuje typy a členy, které musí být k dispozici na konkrétní implementace rozhraní .NET, které odpovídají verzi standard.</span><span class="sxs-lookup"><span data-stu-id="7dc12-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="7dc12-105">Ale .NET Standard není definován, zda je typ serializovat.</span><span class="sxs-lookup"><span data-stu-id="7dc12-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="7dc12-106">Typy definované ve standardní knihovně .NET nejsou označené <xref:System.SerializableAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="7dc12-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="7dc12-107">Místo toho jsou konkrétní implementace .NET, jako je například rozhraní .NET Framework a .NET Core, rozhodnout, zda je určitý typ serializovat.</span><span class="sxs-lookup"><span data-stu-id="7dc12-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="7dc12-108">Pokud jste vytvořili knihovnu, který cílí na .NET Standard, knihovny mohou využívat všechny implementace .NET, který podporuje .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="7dc12-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="7dc12-109">To znamená, že nelze víte předem, zda je určitý typ serializovatelný; pouze můžete určit, zda je serializovatelný v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7dc12-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="7dc12-110">Můžete určit, zda je objekt za běhu serializovatelný načtením hodnoty <xref:System.Type.IsSerializable> vlastnost <xref:System.Type> objekt, který představuje typ tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="7dc12-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="7dc12-111">V následujícím příkladu poskytuje jedna implementace.</span><span class="sxs-lookup"><span data-stu-id="7dc12-111">The following example provides one implementation.</span></span> <span data-ttu-id="7dc12-112">Definuje `IsSerializable(Object)` rozšiřující metoda, která označuje, zda se mají <xref:System.Object> lze serializovat instance.</span><span class="sxs-lookup"><span data-stu-id="7dc12-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="7dc12-113">Libovolný objekt můžete předat metodě k určení, zda ho může serializaci a deserializaci na aktuální implementace .NET, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="7dc12-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="7dc12-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7dc12-114">See also</span></span>

- [<span data-ttu-id="7dc12-115">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="7dc12-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
