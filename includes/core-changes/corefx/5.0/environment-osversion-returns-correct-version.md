---
ms.openlocfilehash: ccd056f23d26e6cce4cc691542784792bffe9fc6
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558170"
---
### <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="5ee35-101">Environment. OSVersion vrátí správnou verzi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="5ee35-101">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="5ee35-102"><xref:System.Environment.OSVersion?displayProperty=nameWithType> Vrátí skutečnou verzi operačního systému (OS), nikoli například operační systém, který je vybrán pro kompatibilitu aplikací.</span><span class="sxs-lookup"><span data-stu-id="5ee35-102"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5ee35-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="5ee35-103">Change description</span></span>

<span data-ttu-id="5ee35-104">V předchozích verzích rozhraní .NET <xref:System.Environment.OSVersion?displayProperty=nameWithType> vrátí verzi operačního systému, která může být nesprávná, pokud je aplikace spuštěna v režimu kompatibility systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5ee35-104">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="5ee35-105">Další informace naleznete v tématu [GetVersionExA Function poznámky](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span><span class="sxs-lookup"><span data-stu-id="5ee35-105">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span>

<span data-ttu-id="5ee35-106">Počínaje platformou .NET 5,0 <xref:System.Environment.OSVersion?displayProperty=nameWithType> vrátí aktuální verzi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="5ee35-106">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5ee35-107">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="5ee35-107">Reason for change</span></span>

<span data-ttu-id="5ee35-108">Uživatelé této vlastnosti očekávají, že vrátí skutečnou verzi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="5ee35-108">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="5ee35-109">Většina aplikací .NET neurčuje jejich podporovanou verzi v manifestu aplikace, a proto z hostitele dotnet Získá výchozí podporovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="5ee35-109">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="5ee35-110">V důsledku toho je překrytí kompatibility pro aplikaci, na které běží, zřídka smysluplné.</span><span class="sxs-lookup"><span data-stu-id="5ee35-110">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="5ee35-111">Když systém Windows uvolní novou verzi a starší hostitel dotnet se pořád používá, můžou tyto aplikace získat nesprávnou verzi operačního systému.</span><span class="sxs-lookup"><span data-stu-id="5ee35-111">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="5ee35-112">Vrácení skutečné verze je v rámci očekávání vývojářů tohoto rozhraní API více vložené.</span><span class="sxs-lookup"><span data-stu-id="5ee35-112">Returning the actual version is more inline with developers' expectations of this API.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5ee35-113">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5ee35-113">Version introduced</span></span>

<span data-ttu-id="5ee35-114">5.0</span><span class="sxs-lookup"><span data-stu-id="5ee35-114">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5ee35-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5ee35-115">Recommended action</span></span>

<span data-ttu-id="5ee35-116">Zkontrolujte a otestujte jakýkoli kód, který používá <xref:System.Environment.OSVersion?displayProperty=nameWithType> k zajištění toho, aby se choval podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="5ee35-116">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

#### <a name="category"></a><span data-ttu-id="5ee35-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5ee35-117">Category</span></span>

<span data-ttu-id="5ee35-118">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="5ee35-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5ee35-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5ee35-119">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Environment.OSVersion`

-->
