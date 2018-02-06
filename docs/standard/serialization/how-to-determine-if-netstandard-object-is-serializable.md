---
title: "Postupy: určit, zda je serializovatelný objekt .NET Standard"
description: "Ukazuje, jak určit, zda lze serializovat typu .NET Standard v době běhu."
ms.custom: 
ms.date: 10/20/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8246e825202b3eb02db5d11f1fe55b4a0d14a4ea
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2018
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="29ade-103">Postupy: určit, zda je serializovatelný objekt .NET Standard</span><span class="sxs-lookup"><span data-stu-id="29ade-103">How to: Determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="29ade-104">.NET Standard je specifikace, která určuje typy a členy, které musí být na konkrétní implementace rozhraní .NET, které odpovídat příslušné verzi nástroje standard.</span><span class="sxs-lookup"><span data-stu-id="29ade-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="29ade-105">Ale .NET Standard nedefinuje zda je typu serializable.</span><span class="sxs-lookup"><span data-stu-id="29ade-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="29ade-106">Typy definované v standardní knihovny .NET nejsou označené jako <xref:System.SerializableAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="29ade-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="29ade-107">Konkrétní implementace rozhraní .NET, například rozhraní .NET Framework a .NET Core, místo toho mohou rozhodnout, zda je konkrétní typ serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="29ade-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="29ade-108">Když jste vyvinutý knihovny s cílem .NET Standard, vaše knihovna mohou být spotřebovávána žádné implementace rozhraní .NET, která podporuje .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="29ade-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="29ade-109">To znamená, že nelze znát předem zda je konkrétní typ serializovatelný; pouze můžete zjistit, zda je serializovatelný za běhu.</span><span class="sxs-lookup"><span data-stu-id="29ade-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="29ade-110">Můžete určit, zda je objekt serializovatelný za běhu načtením hodnotu <xref:System.Type.IsSerializable> vlastnost <xref:System.Type> objekt, který představuje typ tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="29ade-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="29ade-111">Následující příklad poskytuje jednu implementaci.</span><span class="sxs-lookup"><span data-stu-id="29ade-111">The following example provides one implementation.</span></span> <span data-ttu-id="29ade-112">Definuje, `IsSerializable(Object)` metoda rozšíření, která určuje, zda se mají <xref:System.Object> instance lze serializovat.</span><span class="sxs-lookup"><span data-stu-id="29ade-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="29ade-113">Jakýkoli objekt můžete poté předat metodě k určení, zda lze serializovat a deserializovat na aktuální implementace rozhraní .NET, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="29ade-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

# <a name="see-also"></a><span data-ttu-id="29ade-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="29ade-114">See also</span></span>

<span data-ttu-id="29ade-115">[Binární serializace](binary-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="29ade-115">[Binary serialization](binary-serialization.md) </span></span>  
<span data-ttu-id="29ade-116"><xref:System.SerializableAttribute?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="29ade-116"><xref:System.SerializableAttribute?displayProperty=nameWithType></span></span>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
