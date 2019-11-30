---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568103"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="57aa0-101">InvalidAsynchronousStateException – přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="57aa0-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="57aa0-102">Třída <xref:System.ComponentModel.InvalidAsynchronousStateException> byla přesunuta.</span><span class="sxs-lookup"><span data-stu-id="57aa0-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="57aa0-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="57aa0-103">Change description</span></span>

<span data-ttu-id="57aa0-104">V rozhraní .NET Core 2,2 a starších verzích se třída <xref:System.ComponentModel.InvalidAsynchronousStateException> nachází v sestavení *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="57aa0-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="57aa0-105">Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ComponentModel. primitivs* .</span><span class="sxs-lookup"><span data-stu-id="57aa0-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="57aa0-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="57aa0-106">Version introduced</span></span>

<span data-ttu-id="57aa0-107">3,0</span><span class="sxs-lookup"><span data-stu-id="57aa0-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="57aa0-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="57aa0-108">Recommended action</span></span>

<span data-ttu-id="57aa0-109">Tato změna ovlivní pouze aplikace, které používají reflexe k načtení <xref:System.ComponentModel.InvalidAsynchronousStateException> voláním metody, jako je například <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>, která předpokládá, že typ je v konkrétním sestavení.</span><span class="sxs-lookup"><span data-stu-id="57aa0-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="57aa0-110">Pokud je to tento případ, sestavení, na které se odkazuje v volání metody, by mělo být aktualizováno tak, aby odráželo nové umístění sestavení typu.</span><span class="sxs-lookup"><span data-stu-id="57aa0-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="57aa0-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="57aa0-111">Category</span></span>

<span data-ttu-id="57aa0-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="57aa0-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="57aa0-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="57aa0-113">Affected APIs</span></span>

- <span data-ttu-id="57aa0-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="57aa0-114">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
