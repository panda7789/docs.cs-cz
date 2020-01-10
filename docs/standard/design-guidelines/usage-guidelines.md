---
title: Pokyny k používání
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: 57f6600f60e99c72b72c9f82856dc9eb631a9d4b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708994"
---
# <a name="usage-guidelines"></a><span data-ttu-id="677f0-102">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="677f0-102">Usage guidelines</span></span>

<span data-ttu-id="677f0-103">Tato část obsahuje pokyny pro použití běžných typů ve veřejně přístupných rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="677f0-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="677f0-104">Zabývá se přímým využitím integrovaných typů rozhraní (např. atributy serializace) a přetížení běžných operátorů.</span><span class="sxs-lookup"><span data-stu-id="677f0-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="677f0-105">Rozhraní <xref:System.IDisposable?displayProperty=nameWithType> není zahrnuté v této části, ale je popsáno v části [vzor Dispose](../garbage-collection/implementing-dispose.md) .</span><span class="sxs-lookup"><span data-stu-id="677f0-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../garbage-collection/implementing-dispose.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="677f0-106">Pokyny a další informace o dalších běžných integrovaných typech .NET Framework najdete v referenčních tématech následujících: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="677f0-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="677f0-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="677f0-107">In this section</span></span>

[<span data-ttu-id="677f0-108">Pole</span><span class="sxs-lookup"><span data-stu-id="677f0-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="677f0-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="677f0-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="677f0-110">Kolekce</span><span class="sxs-lookup"><span data-stu-id="677f0-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="677f0-111">Serializace</span><span class="sxs-lookup"><span data-stu-id="677f0-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="677f0-112">Použití System.Xml</span><span class="sxs-lookup"><span data-stu-id="677f0-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="677f0-113">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="677f0-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="677f0-114">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="677f0-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="677f0-115">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="677f0-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="677f0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="677f0-116">See also</span></span>

- [<span data-ttu-id="677f0-117">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="677f0-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
