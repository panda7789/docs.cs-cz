---
ms.openlocfilehash: 78678b4b352bb063d1521e9aee3492c0cee059b8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721592"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="8e194-101">InvalidAsynchronousStateException – přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="8e194-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="8e194-102"><xref:System.ComponentModel.InvalidAsynchronousStateException>Třída byla přesunuta.</span><span class="sxs-lookup"><span data-stu-id="8e194-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8e194-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="8e194-103">Change description</span></span>

<span data-ttu-id="8e194-104">V rozhraní .NET Core 2,2 a starších verzích se <xref:System.ComponentModel.InvalidAsynchronousStateException> Třída nachází v sestavení *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="8e194-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="8e194-105">Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ComponentModel. primitivs* .</span><span class="sxs-lookup"><span data-stu-id="8e194-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8e194-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="8e194-106">Version introduced</span></span>

<span data-ttu-id="8e194-107">3.0</span><span class="sxs-lookup"><span data-stu-id="8e194-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8e194-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="8e194-108">Recommended action</span></span>

<span data-ttu-id="8e194-109">Tato změna ovlivní pouze aplikace, které používají reflexe k načtení <xref:System.ComponentModel.InvalidAsynchronousStateException> voláním metody, jako <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> je nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> , které předpokládá, že typ je v konkrétním sestavení.</span><span class="sxs-lookup"><span data-stu-id="8e194-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="8e194-110">V takovém případě aktualizujte sestavení odkazované v volání metody, aby odráželo umístění nového sestavení typu.</span><span class="sxs-lookup"><span data-stu-id="8e194-110">If that is the case, update the assembly referenced in the method call to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="8e194-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="8e194-111">Category</span></span>

<span data-ttu-id="8e194-112">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="8e194-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8e194-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8e194-113">Affected APIs</span></span>

<span data-ttu-id="8e194-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="8e194-114">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->
