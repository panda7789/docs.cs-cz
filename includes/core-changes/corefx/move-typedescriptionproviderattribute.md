---
ms.openlocfilehash: 4fbec1028b6d75b90d4638814c877c263c8c8936
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182041"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="481f5-101">TypeDescriptionProviderAttribute přesunuté do jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="481f5-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="481f5-102"><xref:System.ComponentModel.TypeDescriptionProviderAttribute> Třída byla přesunuta.</span><span class="sxs-lookup"><span data-stu-id="481f5-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="481f5-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="481f5-103">Change description</span></span>

<span data-ttu-id="481f5-104">V rozhraní .NET Core 2,2 a starších verzích <xref:System.ComponentModel.TypeDescriptionProviderAttribute> se Třída nachází v sestavení *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="481f5-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="481f5-105">Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ObjectModel* .</span><span class="sxs-lookup"><span data-stu-id="481f5-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="481f5-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="481f5-106">Version introduced</span></span>

<span data-ttu-id="481f5-107">3.0</span><span class="sxs-lookup"><span data-stu-id="481f5-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="481f5-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="481f5-108">Recommended action</span></span>

<span data-ttu-id="481f5-109">Tato změna ovlivní pouze aplikace, které používají reflexe <xref:System.ComponentModel.TypeDescriptionProviderAttribute> k načtení typu voláním metody <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> , jako je nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> , které předpokládá, že typ je v konkrétním sestavení.</span><span class="sxs-lookup"><span data-stu-id="481f5-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="481f5-110">V takovém případě by se sestavení odkazované v volání metody mělo aktualizovat tak, aby odráželo nové umístění sestavení typu.</span><span class="sxs-lookup"><span data-stu-id="481f5-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="481f5-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="481f5-111">Category</span></span>

<span data-ttu-id="481f5-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="481f5-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="481f5-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="481f5-113">Affected APIs</span></span>

- <span data-ttu-id="481f5-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="481f5-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->