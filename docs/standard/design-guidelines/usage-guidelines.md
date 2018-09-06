---
title: Pokyny k používání
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04e44a6b58fd334b6a23e113922b980f69de627b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869863"
---
# <a name="usage-guidelines"></a><span data-ttu-id="c9a98-102">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="c9a98-102">Usage guidelines</span></span>

<span data-ttu-id="c9a98-103">Tato část obsahuje pokyny k používání běžných typů ve veřejně dostupná rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="c9a98-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="c9a98-104">Zabývá přímého použití předdefinované typy rozhraní Framework (např. atributy serializace) a běžné operátory přetížení.</span><span class="sxs-lookup"><span data-stu-id="c9a98-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="c9a98-105"><xref:System.IDisposable?displayProperty=nameWithType> Rozhraní není uvedenými v této části, ale je podrobněji popsána [vzor Dispose](../../../docs/standard/design-guidelines/dispose-pattern.md) oddílu.</span><span class="sxs-lookup"><span data-stu-id="c9a98-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="c9a98-106">Pokyny a další informace o dalších běžných vestavěné typy rozhraní .NET Framework, naleznete v tématu referenční témata pro následující: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c9a98-106">For guidelines and additional information about about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c9a98-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c9a98-107">In this section</span></span>

[<span data-ttu-id="c9a98-108">Pole</span><span class="sxs-lookup"><span data-stu-id="c9a98-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="c9a98-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="c9a98-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="c9a98-110">Kolekce</span><span class="sxs-lookup"><span data-stu-id="c9a98-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="c9a98-111">Serializace</span><span class="sxs-lookup"><span data-stu-id="c9a98-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="c9a98-112">Použití System.Xml</span><span class="sxs-lookup"><span data-stu-id="c9a98-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="c9a98-113">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="c9a98-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="c9a98-114">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="c9a98-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="c9a98-115">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="c9a98-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c9a98-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9a98-116">See also</span></span>

- [<span data-ttu-id="c9a98-117">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="c9a98-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
