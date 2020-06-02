---
title: Jak zjistit, zda je objekt .NET Standard serializovatelný
description: Ukazuje, jak určit, zda lze typ .NET Standard serializovat v době běhu.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: b6791ae0666aeb0ac02d8a38ca419d7de2b263cf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289600"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="ac776-103">Jak zjistit, zda je objekt .NET Standard serializovatelný</span><span class="sxs-lookup"><span data-stu-id="ac776-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="ac776-104">.NET Standard je specifikace definující typy a členy, které musí být přítomny v konkrétních implementacích .NET, které odpovídají této verzi standardu.</span><span class="sxs-lookup"><span data-stu-id="ac776-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="ac776-105">.NET Standard však nedefinuje, zda je typ serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="ac776-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="ac776-106">Typy definované v knihovně .NET Standard nejsou označeny <xref:System.SerializableAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="ac776-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="ac776-107">Místo toho je možné určit, zda je konkrétní typ serializovatelný, konkrétní implementaci rozhraní .NET, například .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ac776-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span>

<span data-ttu-id="ac776-108">Pokud jste vytvořili knihovnu, která cílí na .NET Standard, vaše knihovna může být spotřebována jakoukoli implementací .NET, která podporuje .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ac776-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="ac776-109">To znamená, že nemůžete předem znát, zda je konkrétní typ serializovatelný; můžete určit, zda je v době běhu serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="ac776-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="ac776-110">Můžete určit, zda je objekt serializovatelný za běhu načtením hodnoty <xref:System.Type.IsSerializable> vlastnosti <xref:System.Type> objektu, který představuje typ daného objektu.</span><span class="sxs-lookup"><span data-stu-id="ac776-110">You can determine whether an object is serializable at run time by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="ac776-111">Následující příklad poskytuje jednu implementaci.</span><span class="sxs-lookup"><span data-stu-id="ac776-111">The following example provides one implementation.</span></span> <span data-ttu-id="ac776-112">Definuje `IsSerializable(Object)` metodu rozšíření, která označuje, zda <xref:System.Object> může být jakákoli instance serializována.</span><span class="sxs-lookup"><span data-stu-id="ac776-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="ac776-113">Pak můžete předat libovolný objekt metodě, abyste zjistili, zda lze serializovat a deserializovat v aktuální implementaci rozhraní .NET, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ac776-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="ac776-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac776-114">See also</span></span>

- [<span data-ttu-id="ac776-115">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="ac776-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
