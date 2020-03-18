---
ms.openlocfilehash: 19359422f79f8240676b0057c7391f6b06f961ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147546"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="02b52-101">InvalidAsynchronousStateException přesunuta do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="02b52-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="02b52-102">Třída <xref:System.ComponentModel.InvalidAsynchronousStateException> byla přesunuta.</span><span class="sxs-lookup"><span data-stu-id="02b52-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="02b52-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="02b52-103">Change description</span></span>

<span data-ttu-id="02b52-104">V rozhraní .NET Core 2.2 <xref:System.ComponentModel.InvalidAsynchronousStateException> a starších verzích se třída nachází v sestavě *System.ComponentModel.TypeConverter.*</span><span class="sxs-lookup"><span data-stu-id="02b52-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="02b52-105">Počínaje rozhraním .NET Core 3.0 se nachází v sestavě *System.ComponentModel.Primitives.*</span><span class="sxs-lookup"><span data-stu-id="02b52-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="02b52-106">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="02b52-106">Version introduced</span></span>

<span data-ttu-id="02b52-107">3.0</span><span class="sxs-lookup"><span data-stu-id="02b52-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="02b52-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="02b52-108">Recommended action</span></span>

<span data-ttu-id="02b52-109">Tato změna má vliv pouze na <xref:System.ComponentModel.InvalidAsynchronousStateException> aplikace, které <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> používají reflexe <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> načíst voláním metody, jako je například nebo přetížení, které předpokládá, že typ je v určitém sestavení.</span><span class="sxs-lookup"><span data-stu-id="02b52-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="02b52-110">Pokud tomu tak je, sestavení sestavení odkazuje ve volání metody by měla být aktualizována tak, aby odrážely nové umístění sestavení typu.</span><span class="sxs-lookup"><span data-stu-id="02b52-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="02b52-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="02b52-111">Category</span></span>

<span data-ttu-id="02b52-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="02b52-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="02b52-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="02b52-113">Affected APIs</span></span>

<span data-ttu-id="02b52-114">Žádné.</span><span class="sxs-lookup"><span data-stu-id="02b52-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
