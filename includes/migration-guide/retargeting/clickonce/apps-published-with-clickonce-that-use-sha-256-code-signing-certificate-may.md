---
ms.openlocfilehash: 416590c7bd959eea011b7e7c5db48f22d349d0f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615635"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a><span data-ttu-id="25613-101">Aplikace publikované pomocí ClickOnce, které používají certifikát SHA-256, můžou selhat ve Windows 2003</span><span class="sxs-lookup"><span data-stu-id="25613-101">Apps published with ClickOnce that use a SHA-256 code-signing certificate may fail on Windows 2003</span></span>

#### <a name="details"></a><span data-ttu-id="25613-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="25613-102">Details</span></span>

<span data-ttu-id="25613-103">Spustitelný soubor je podepsaný pomocí SHA256.</span><span class="sxs-lookup"><span data-stu-id="25613-103">The executable is signed with SHA256.</span></span> <span data-ttu-id="25613-104">Dříve byla podepsána pomocí SHA1 bez ohledu na to, zda byl certifikát pro podpis kódu SHA-1 nebo SHA-256.</span><span class="sxs-lookup"><span data-stu-id="25613-104">Previously, it was signed with SHA1 regardless of whether the code-signing certificate was SHA-1 or SHA-256.</span></span> <span data-ttu-id="25613-105">To platí pro:</span><span class="sxs-lookup"><span data-stu-id="25613-105">This applies to:</span></span>

- <span data-ttu-id="25613-106">Všechny aplikace vytvořené pomocí sady Visual Studio 2012 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="25613-106">All applications built with Visual Studio 2012 or later.</span></span>
- <span data-ttu-id="25613-107">Aplikace vytvořené pomocí sady Visual Studio 2010 nebo starší v systémech s .NET Framework 4,5 k dispozici.</span><span class="sxs-lookup"><span data-stu-id="25613-107">Applications built with Visual Studio 2010 or earlier on systems with the .NET Framework 4.5 present.</span></span>
<span data-ttu-id="25613-108">Kromě toho, pokud je k dispozici .NET Framework 4,5 nebo novější, manifest ClickOnce je také podepsán pomocí algoritmu SHA-256 pro certifikáty SHA-256 bez ohledu na .NET Framework verzi, proti které byla zkompilována.</span><span class="sxs-lookup"><span data-stu-id="25613-108">In addition, if the .NET Framework 4.5 or later is present, the ClickOnce manifest is also signed with SHA-256 for SHA-256 certificates regardless of the .NET Framework version against which it was compiled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="25613-109">Návrh</span><span class="sxs-lookup"><span data-stu-id="25613-109">Suggestion</span></span>

<span data-ttu-id="25613-110">Změna v podepisování spustitelného souboru ClickOnce ovlivní pouze systémy Windows Server 2003; vyžadují instalaci znalostní báze KB 938397.</span><span class="sxs-lookup"><span data-stu-id="25613-110">The change in signing the ClickOnce executable affects only Windows Server 2003 systems; they require that KB 938397 be installed.</span></span> <span data-ttu-id="25613-111">Změna v podepisování manifestu pomocí SHA-256 i v případě, že aplikace cílí na .NET Framework 4,0 nebo starší verze představuje závislost modulu runtime na .NET Framework 4,5 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="25613-111">The change in signing the manifest with SHA-256 even when an app targets the .NET Framework 4.0 or earlier versions introduces a runtime dependency on the .NET Framework 4.5 or a later version.</span></span>

| <span data-ttu-id="25613-112">Name</span><span class="sxs-lookup"><span data-stu-id="25613-112">Name</span></span>    | <span data-ttu-id="25613-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="25613-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="25613-114">Rozsah</span><span class="sxs-lookup"><span data-stu-id="25613-114">Scope</span></span>   | <span data-ttu-id="25613-115">Edge</span><span class="sxs-lookup"><span data-stu-id="25613-115">Edge</span></span>        |
| <span data-ttu-id="25613-116">Verze</span><span class="sxs-lookup"><span data-stu-id="25613-116">Version</span></span> | <span data-ttu-id="25613-117">4.5</span><span class="sxs-lookup"><span data-stu-id="25613-117">4.5</span></span>         |
| <span data-ttu-id="25613-118">Typ</span><span class="sxs-lookup"><span data-stu-id="25613-118">Type</span></span>    | <span data-ttu-id="25613-119">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="25613-119">Retargeting</span></span> |
