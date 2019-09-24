---
ms.openlocfilehash: 4d479636f41095610eaf39f92ad0dad4863ab8b5
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216339"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="3553e-101">TypeDescriptionProviderAttribute přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="3553e-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="3553e-102"><xref:System.ComponentModel.TypeDescriptionProviderAttribute> Třída byla přesunuta.</span><span class="sxs-lookup"><span data-stu-id="3553e-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3553e-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="3553e-103">Change description</span></span>

<span data-ttu-id="3553e-104">V rozhraní .NET Core 2,2 a starších verzích <xref:System.ComponentModel.TypeDescriptionProviderAttribute> se Třída nachází v sestavení *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="3553e-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="3553e-105">Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ObjectModel* .</span><span class="sxs-lookup"><span data-stu-id="3553e-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3553e-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="3553e-106">Version introduced</span></span>

<span data-ttu-id="3553e-107">3.0</span><span class="sxs-lookup"><span data-stu-id="3553e-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3553e-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="3553e-108">Recommended action</span></span>

<span data-ttu-id="3553e-109">Tato změna ovlivní pouze aplikace, které používají reflexe <xref:System.ComponentModel.TypeDescriptionProviderAttribute> k načtení typu voláním metody <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> , jako je nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> , které předpokládá, že typ je v konkrétním sestavení.</span><span class="sxs-lookup"><span data-stu-id="3553e-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="3553e-110">V takovém případě by se sestavení odkazované v volání metody mělo aktualizovat tak, aby odráželo nové umístění sestavení typu.</span><span class="sxs-lookup"><span data-stu-id="3553e-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="3553e-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="3553e-111">Category</span></span>

<span data-ttu-id="3553e-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3553e-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3553e-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3553e-113">Affected APIs</span></span>

- <span data-ttu-id="3553e-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="3553e-114">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
