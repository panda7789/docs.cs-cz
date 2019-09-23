---
ms.openlocfilehash: 4b41e5fcb6da638457ca8029a635f391b6a7b8ec
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182010"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="2a304-101">InvalidAsynchronousStateException – přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="2a304-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="2a304-102"><xref:System.ComponentModel.InvalidAsynchronousStateException> Třída byla přesunuta.</span><span class="sxs-lookup"><span data-stu-id="2a304-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2a304-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="2a304-103">Change description</span></span>

<span data-ttu-id="2a304-104">V rozhraní .NET Core 2,2 a starších verzích <xref:System.ComponentModel.InvalidAsynchronousStateException> se Třída nachází v sestavení *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="2a304-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="2a304-105">Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ComponentModel. primitivs* .</span><span class="sxs-lookup"><span data-stu-id="2a304-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2a304-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="2a304-106">Version introduced</span></span>

<span data-ttu-id="2a304-107">3.0</span><span class="sxs-lookup"><span data-stu-id="2a304-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2a304-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="2a304-108">Recommended action</span></span>

<span data-ttu-id="2a304-109">Tato změna ovlivní pouze aplikace, které používají reflexe <xref:System.ComponentModel.InvalidAsynchronousStateException> k načtení voláním metody <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> , jako je nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> , které předpokládá, že typ je v konkrétním sestavení.</span><span class="sxs-lookup"><span data-stu-id="2a304-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="2a304-110">Pokud je to tento případ, sestavení, na které se odkazuje v volání metody, by mělo být aktualizováno tak, aby odráželo nové umístění sestavení typu.</span><span class="sxs-lookup"><span data-stu-id="2a304-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="2a304-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2a304-111">Category</span></span>

<span data-ttu-id="2a304-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="2a304-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2a304-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2a304-113">Affected APIs</span></span>

- <span data-ttu-id="2a304-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="2a304-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->