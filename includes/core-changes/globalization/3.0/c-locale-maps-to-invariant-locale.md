---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567760"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="bb396-101">Národní prostředí "C" mapuje na invariantní národní prostředí</span><span class="sxs-lookup"><span data-stu-id="bb396-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="bb396-102">.NET Core 2.2 a starší verze závisí na výchozí chování JIP, který mapuje národní prostředí "C" na en_US_POSIX národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="bb396-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="bb396-103">Národní prostředí en_US_POSIX má nežádoucí řazení chování, protože nepodporuje porovnání řetězců bez rozlišování velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="bb396-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="bb396-104">Vzhledem k tomu, že některé distribuce Linuxu nastavují národní prostředí "C" jako výchozí národní prostředí, uživatelé měli neočekávané chování.</span><span class="sxs-lookup"><span data-stu-id="bb396-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bb396-105">Popis změny</span><span class="sxs-lookup"><span data-stu-id="bb396-105">Change description</span></span>

<span data-ttu-id="bb396-106">Počínaje rozhraním .NET Core 3.0 se mapování národního prostředí "C" změnilo tak, aby místo en_US_POSIX používalo národní prostředí Invariant.</span><span class="sxs-lookup"><span data-stu-id="bb396-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="bb396-107">Národní prostředí "C" invariantní mapování je také použita pro windows konzistence.</span><span class="sxs-lookup"><span data-stu-id="bb396-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="bb396-108">Mapování "C" na en_US_POSIX kultury způsobilzmatek zákazníka, protože en_US_POSIX nepodporuje operace řazení a vyhledávání bez rozlišování malých a velkých písmen.</span><span class="sxs-lookup"><span data-stu-id="bb396-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="bb396-109">Vzhledem k tomu, že národní prostředí "C" se používá jako výchozí národní prostředí v některých distribucích Linuxu, zákazníci zažili toto nežádoucí chování v těchto operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="bb396-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bb396-110">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="bb396-110">Version introduced</span></span>

<span data-ttu-id="bb396-111">3.0</span><span class="sxs-lookup"><span data-stu-id="bb396-111">3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="bb396-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="bb396-112">Recommended action</span></span>

<span data-ttu-id="bb396-113">Nic konkrétního víc než povědomí o této změně.</span><span class="sxs-lookup"><span data-stu-id="bb396-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="bb396-114">Tato změna se týká pouze aplikací, které používají mapování národního prostředí "C".</span><span class="sxs-lookup"><span data-stu-id="bb396-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="bb396-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="bb396-115">Category</span></span>

<span data-ttu-id="bb396-116">Globalizace</span><span class="sxs-lookup"><span data-stu-id="bb396-116">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="bb396-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bb396-117">Affected APIs</span></span>

<span data-ttu-id="bb396-118">Všechna kolace a jazyková prostředí API jsou ovlivněny touto změnou.</span><span class="sxs-lookup"><span data-stu-id="bb396-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->
