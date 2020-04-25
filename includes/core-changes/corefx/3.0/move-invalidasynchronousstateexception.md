---
ms.openlocfilehash: d1562cb76f37b6cc2aeb6fe2f7c17c393e169e84
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158467"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="b54a6-101">InvalidAsynchronousStateException – přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="b54a6-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="b54a6-102"><xref:System.ComponentModel.InvalidAsynchronousStateException> Třída byla přesunuta.</span><span class="sxs-lookup"><span data-stu-id="b54a6-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b54a6-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="b54a6-103">Change description</span></span>

<span data-ttu-id="b54a6-104">V rozhraní .NET Core 2,2 a starších verzích se <xref:System.ComponentModel.InvalidAsynchronousStateException> Třída nachází v sestavení *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="b54a6-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="b54a6-105">Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ComponentModel. primitivs* .</span><span class="sxs-lookup"><span data-stu-id="b54a6-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b54a6-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b54a6-106">Version introduced</span></span>

<span data-ttu-id="b54a6-107">3.0</span><span class="sxs-lookup"><span data-stu-id="b54a6-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b54a6-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b54a6-108">Recommended action</span></span>

<span data-ttu-id="b54a6-109">Tato změna ovlivní pouze aplikace, které používají reflexe <xref:System.ComponentModel.InvalidAsynchronousStateException> k načtení voláním metody, <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> jako je nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> , které předpokládá, že typ je v konkrétním sestavení.</span><span class="sxs-lookup"><span data-stu-id="b54a6-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="b54a6-110">V takovém případě aktualizujte sestavení odkazované v volání metody, aby odráželo umístění nového sestavení typu.</span><span class="sxs-lookup"><span data-stu-id="b54a6-110">If that is the case, update the assembly referenced in the method call to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="b54a6-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b54a6-111">Category</span></span>

<span data-ttu-id="b54a6-112">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="b54a6-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b54a6-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b54a6-113">Affected APIs</span></span>

<span data-ttu-id="b54a6-114">Žádné.</span><span class="sxs-lookup"><span data-stu-id="b54a6-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
