---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420422"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a><span data-ttu-id="4a544-101">Process. StartInfo vyvolá InvalidOperationException pro procesy, které jste nespustili.</span><span class="sxs-lookup"><span data-stu-id="4a544-101">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>

<span data-ttu-id="4a544-102">Čtení <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> vlastnosti pro procesy, které nespustil váš kód, vyvolá výjimku <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="4a544-102">Reading the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start throws an <xref:System.InvalidOperationException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4a544-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="4a544-103">Change description</span></span>

<span data-ttu-id="4a544-104">V .NET Framework přístup k <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> vlastnosti pro procesy, které nespustil váš kód, vrátí zástupný <xref:System.Diagnostics.ProcessStartInfo> objekt.</span><span class="sxs-lookup"><span data-stu-id="4a544-104">In .NET Framework, accessing the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start returns a dummy <xref:System.Diagnostics.ProcessStartInfo> object.</span></span> <span data-ttu-id="4a544-105">Zástupný objekt obsahuje výchozí hodnoty pro všechny jeho vlastnosti s výjimkou <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> .</span><span class="sxs-lookup"><span data-stu-id="4a544-105">The dummy object contains default values for all of its properties except <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables>.</span></span>

<span data-ttu-id="4a544-106">Pokud v .NET Core 1,0 přečtete <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> vlastnost pro proces, který jste nespustili (to znamená voláním <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> ), <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="4a544-106">Starting in .NET Core 1.0, if you read the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for a process that you didn't start (that is, by calling <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>), an <xref:System.InvalidOperationException> is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4a544-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="4a544-107">Version introduced</span></span>

<span data-ttu-id="4a544-108">1.0</span><span class="sxs-lookup"><span data-stu-id="4a544-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4a544-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="4a544-109">Recommended action</span></span>

<span data-ttu-id="4a544-110">Nepoužívejte přístup k <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> vlastnosti pro procesy, které nespustily váš kód.</span><span class="sxs-lookup"><span data-stu-id="4a544-110">Do not access the <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> property for processes that your code didn't start.</span></span> <span data-ttu-id="4a544-111">Například tuto vlastnost nepřečtete pro procesy, které vrátí <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4a544-111">For example, don't read this property for processes returned by <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="4a544-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="4a544-112">Category</span></span>

<span data-ttu-id="4a544-113">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="4a544-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4a544-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4a544-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
