---
ms.openlocfilehash: d35de48dd22003c851cf5dba9e8517ec48b9217b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567760"
---
### <a name="c-locale-maps-to-the-invariant-locale"></a><span data-ttu-id="64bde-101">Národní prostředí jazyka C se mapuje na neutrální národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="64bde-101">"C" locale maps to the invariant locale</span></span>

<span data-ttu-id="64bde-102">.NET Core 2,2 a starší verze závisí na výchozím chování ICU, které mapuje národní prostředí "C" na en_US_POSIX národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="64bde-102">.NET Core 2.2 and earlier versions depend on the default ICU behavior, which maps the "C" locale to the en_US_POSIX locale.</span></span> <span data-ttu-id="64bde-103">Národní prostředí en_US_POSIX má nežádoucí chování kolace, protože nepodporuje porovnávání řetězců bez rozlišování velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="64bde-103">The en_US_POSIX locale has an undesirable collation behavior, because it doesn't support case-insensitive string comparisons.</span></span> <span data-ttu-id="64bde-104">Vzhledem k tomu, že některá distribuce systému Linux nastavila národní prostředí "C" jako výchozí národní prostředí, došlo k neočekávanému chování uživatelů.</span><span class="sxs-lookup"><span data-stu-id="64bde-104">Because some Linux distributions set the "C" locale as the default locale, users were experiencing unexpected behavior.</span></span>

#### <a name="change-description"></a><span data-ttu-id="64bde-105">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="64bde-105">Change description</span></span>

<span data-ttu-id="64bde-106">Počínaje rozhraním .NET Core 3,0 se mapování národního prostředí "C" změnilo na použití neutrálního národního prostředí namísto en_US_POSIX.</span><span class="sxs-lookup"><span data-stu-id="64bde-106">Starting with .NET Core 3.0, the "C" locale mapping has changed to use the Invariant locale instead of en_US_POSIX.</span></span> <span data-ttu-id="64bde-107">Národní prostředí "C" na invariantní mapování je také použito pro systém Windows pro zajištění konzistence.</span><span class="sxs-lookup"><span data-stu-id="64bde-107">The "C" locale to Invariant mapping is also applied to Windows for consistency.</span></span>

<span data-ttu-id="64bde-108">Mapování "C" na en_US_POSIX jazykové verze způsobilo nejasnost zákazníka, protože en_US_POSIX nepodporuje řazení a vyhledávání operací s řetězci v případě nerozlišování velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="64bde-108">Mapping "C" to en_US_POSIX culture caused customer confusion, because en_US_POSIX doesn't support case insensitive sorting/searching string operations.</span></span> <span data-ttu-id="64bde-109">Vzhledem k tomu, že národní prostředí "C" se používá jako výchozí národní prostředí v některých distribuceích Linux, zákazníci narazili na toto neočekávané chování na tyto operační systémy.</span><span class="sxs-lookup"><span data-stu-id="64bde-109">Because the "C" locale is used as a default locale in some of the Linux distros, customers experienced this undesired behavior on these operating systems.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="64bde-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="64bde-110">Version introduced</span></span>

<span data-ttu-id="64bde-111">3,0</span><span class="sxs-lookup"><span data-stu-id="64bde-111">3.0</span></span>

### <a name="recommended-action"></a><span data-ttu-id="64bde-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="64bde-112">Recommended action</span></span>

<span data-ttu-id="64bde-113">Nic nespecifické pro víc, než je povědomí o této změně.</span><span class="sxs-lookup"><span data-stu-id="64bde-113">Nothing specific more than the awareness of this change.</span></span> <span data-ttu-id="64bde-114">Tato změna ovlivní pouze aplikace, které používají mapování národního prostředí "C".</span><span class="sxs-lookup"><span data-stu-id="64bde-114">This change affects only applications that use the "C" locale mapping.</span></span>

### <a name="category"></a><span data-ttu-id="64bde-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="64bde-115">Category</span></span>

<span data-ttu-id="64bde-116">Globalizace</span><span class="sxs-lookup"><span data-stu-id="64bde-116">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="64bde-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="64bde-117">Affected APIs</span></span>

<span data-ttu-id="64bde-118">Tato změna ovlivní všechna rozhraní API pro kolaci a kulturu.</span><span class="sxs-lookup"><span data-stu-id="64bde-118">All collation and culture APIs are affected by this change.</span></span>

<!--

-->
