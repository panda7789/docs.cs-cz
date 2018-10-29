---
title: Pokyny k používání
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e583bf7768c60477effb6c1cf9b838ae4c8c182
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197935"
---
# <a name="usage-guidelines"></a><span data-ttu-id="0a37c-102">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="0a37c-102">Usage guidelines</span></span>

<span data-ttu-id="0a37c-103">Tato část obsahuje pokyny k používání běžných typů ve veřejně dostupná rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="0a37c-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="0a37c-104">Zabývá přímého použití předdefinované typy rozhraní Framework (např. atributy serializace) a běžné operátory přetížení.</span><span class="sxs-lookup"><span data-stu-id="0a37c-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="0a37c-105"><xref:System.IDisposable?displayProperty=nameWithType> Rozhraní není uvedenými v této části, ale je podrobněji popsána [vzor Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md) oddílu.</span><span class="sxs-lookup"><span data-stu-id="0a37c-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="0a37c-106">Pokyny a další informace o dalších běžných vestavěné typy rozhraní .NET Framework, naleznete v tématu referenční témata pro následující: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0a37c-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0a37c-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0a37c-107">In this section</span></span>

[<span data-ttu-id="0a37c-108">Pole</span><span class="sxs-lookup"><span data-stu-id="0a37c-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="0a37c-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="0a37c-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="0a37c-110">Kolekce</span><span class="sxs-lookup"><span data-stu-id="0a37c-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="0a37c-111">Serializace</span><span class="sxs-lookup"><span data-stu-id="0a37c-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="0a37c-112">Použití System.Xml</span><span class="sxs-lookup"><span data-stu-id="0a37c-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="0a37c-113">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="0a37c-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="0a37c-114">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="0a37c-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="0a37c-115">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="0a37c-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0a37c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a37c-116">See also</span></span>

- [<span data-ttu-id="0a37c-117">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="0a37c-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
