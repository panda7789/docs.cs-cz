---
ms.openlocfilehash: 57ca2ad839aab8d61da1a929660920efe1190334
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147533"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="e46e7-101">TypeDescriptionProviderAttribute přesunutdo jiného sestavení</span><span class="sxs-lookup"><span data-stu-id="e46e7-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="e46e7-102">Třída <xref:System.ComponentModel.TypeDescriptionProviderAttribute> byla přesunuta.</span><span class="sxs-lookup"><span data-stu-id="e46e7-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e46e7-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="e46e7-103">Change description</span></span>

<span data-ttu-id="e46e7-104">V rozhraní .NET Core 2.2 <xref:System.ComponentModel.TypeDescriptionProviderAttribute> a starších verzích se třída nachází v sestavě *System.ComponentModel.TypeConverter.*</span><span class="sxs-lookup"><span data-stu-id="e46e7-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="e46e7-105">Počínaje rozhraním .NET Core 3.0 se nachází v sestavení *System.ObjectModel.*</span><span class="sxs-lookup"><span data-stu-id="e46e7-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e46e7-106">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="e46e7-106">Version introduced</span></span>

<span data-ttu-id="e46e7-107">3.0</span><span class="sxs-lookup"><span data-stu-id="e46e7-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e46e7-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e46e7-108">Recommended action</span></span>

<span data-ttu-id="e46e7-109">Tato změna má vliv pouze na <xref:System.ComponentModel.TypeDescriptionProviderAttribute> aplikace, které používají <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> reflexe <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> načíst typ voláním metody, jako je například nebo přetížení, které předpokládá, že typ je v určitém sestavení.</span><span class="sxs-lookup"><span data-stu-id="e46e7-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="e46e7-110">Pokud tomu tak je, sestavení odkazované ve volání metody by měla být aktualizována tak, aby odrážela nové umístění sestavení typu.</span><span class="sxs-lookup"><span data-stu-id="e46e7-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="e46e7-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e46e7-111">Category</span></span>

<span data-ttu-id="e46e7-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e46e7-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e46e7-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e46e7-113">Affected APIs</span></span>

<span data-ttu-id="e46e7-114">Žádné.</span><span class="sxs-lookup"><span data-stu-id="e46e7-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
