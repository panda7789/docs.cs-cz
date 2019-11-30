---
ms.openlocfilehash: 4d479636f41095610eaf39f92ad0dad4863ab8b5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568238"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="3625e-101">TypeDescriptionProviderAttribute přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="3625e-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="3625e-102">Třída <xref:System.ComponentModel.TypeDescriptionProviderAttribute> byla přesunuta.</span><span class="sxs-lookup"><span data-stu-id="3625e-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3625e-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="3625e-103">Change description</span></span>

<span data-ttu-id="3625e-104">V rozhraní .NET Core 2,2 a starších verzích se třída <xref:System.ComponentModel.TypeDescriptionProviderAttribute> nachází v sestavení *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="3625e-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="3625e-105">Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ObjectModel* .</span><span class="sxs-lookup"><span data-stu-id="3625e-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3625e-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="3625e-106">Version introduced</span></span>

<span data-ttu-id="3625e-107">3,0</span><span class="sxs-lookup"><span data-stu-id="3625e-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3625e-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="3625e-108">Recommended action</span></span>

<span data-ttu-id="3625e-109">Tato změna ovlivní pouze aplikace, které používají reflexe k načtení <xref:System.ComponentModel.TypeDescriptionProviderAttribute> typu voláním metody, jako je například <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>, která předpokládá, že typ je v konkrétním sestavení.</span><span class="sxs-lookup"><span data-stu-id="3625e-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="3625e-110">V takovém případě by se sestavení odkazované v volání metody mělo aktualizovat tak, aby odráželo nové umístění sestavení typu.</span><span class="sxs-lookup"><span data-stu-id="3625e-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="3625e-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="3625e-111">Category</span></span>

<span data-ttu-id="3625e-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3625e-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3625e-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3625e-113">Affected APIs</span></span>

- <span data-ttu-id="3625e-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="3625e-114">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
