---
ms.openlocfilehash: 7a2617f27dfd6bb527ff6d408fae6382075f24ae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721722"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="e2dd8-101">TypeDescriptionProviderAttribute přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="e2dd8-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="e2dd8-102"><xref:System.ComponentModel.TypeDescriptionProviderAttribute>Třída byla přesunuta.</span><span class="sxs-lookup"><span data-stu-id="e2dd8-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e2dd8-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="e2dd8-103">Change description</span></span>

<span data-ttu-id="e2dd8-104">V rozhraní .NET Core 2,2 a starších verzích se <xref:System.ComponentModel.TypeDescriptionProviderAttribute> Třída nachází v sestavení *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="e2dd8-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="e2dd8-105">Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ObjectModel* .</span><span class="sxs-lookup"><span data-stu-id="e2dd8-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e2dd8-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e2dd8-106">Version introduced</span></span>

<span data-ttu-id="e2dd8-107">3.0</span><span class="sxs-lookup"><span data-stu-id="e2dd8-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e2dd8-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e2dd8-108">Recommended action</span></span>

<span data-ttu-id="e2dd8-109">Tato změna ovlivní pouze aplikace, které používají reflexe k načtení <xref:System.ComponentModel.TypeDescriptionProviderAttribute> typu voláním metody, jako <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> je nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> , které předpokládá, že typ je v konkrétním sestavení.</span><span class="sxs-lookup"><span data-stu-id="e2dd8-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="e2dd8-110">V takovém případě by se sestavení odkazované v volání metody mělo aktualizovat tak, aby odráželo nové umístění sestavení typu.</span><span class="sxs-lookup"><span data-stu-id="e2dd8-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="e2dd8-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e2dd8-111">Category</span></span>

<span data-ttu-id="e2dd8-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2dd8-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e2dd8-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e2dd8-113">Affected APIs</span></span>

<span data-ttu-id="e2dd8-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="e2dd8-114">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->
