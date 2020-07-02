---
ms.openlocfilehash: d4f0095bc9fde98087dce528c8154d9c9ac6ddb7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621786"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a><span data-ttu-id="5bdb6-101">Neočekávaným způsobem se kontrola pravopisu WPF nezdařila.</span><span class="sxs-lookup"><span data-stu-id="5bdb6-101">WPF Spell Checking fails in unexpected ways</span></span>

#### <a name="details"></a><span data-ttu-id="5bdb6-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5bdb6-102">Details</span></span>

<span data-ttu-id="5bdb6-103">To zahrnuje řadu potíží s kontrolou pravopisu WPF:</span><span class="sxs-lookup"><span data-stu-id="5bdb6-103">This includes a number of WPF Spell Checker issues:</span></span><ul><li><span data-ttu-id="5bdb6-104">Nástroj pro kontrolu pravopisu WPF někdy vyvolá<xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5bdb6-104">WPF Spell Checker sometimes throws <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span></span></li><li><span data-ttu-id="5bdb6-105">Kontrola pravopisu WPF se nezdařila, <xref:System.UnauthorizedAccessException> Pokud se aplikace spouští pomocí příkazu Spustit jako jiný uživatel.</span><span class="sxs-lookup"><span data-stu-id="5bdb6-105">WPF Spell Checker fails with <xref:System.UnauthorizedAccessException> when applications are launched using 'run as different user'</span></span></li><li><span data-ttu-id="5bdb6-106">Kontrola pravopisu WPF nesprávně identifikuje pravopisné chyby ve složených slovech, jako je ' Hausnummer ' v němčině.</span><span class="sxs-lookup"><span data-stu-id="5bdb6-106">WPF Spell Checker incorrectly identifies spelling errors in compound words like 'Hausnummer' in German.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="5bdb6-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="5bdb6-107">Suggestion</span></span>

<span data-ttu-id="5bdb6-108">Problémová #1 – Toto řešení bylo opraveno v .NET Framework 4.6.2 potíží #2 – Kontrola pravopisu WPF již není podporována, pokud se aplikace spouští pomocí příkazu Spustit jako jiný uživatel.</span><span class="sxs-lookup"><span data-stu-id="5bdb6-108">Issue #1 - This has been fixed in .NET Framework 4.6.2 Issue #2 - WPF Spell Checker is no longer supported when applications are launched using 'run as different user'.</span></span> <span data-ttu-id="5bdb6-109">Spuštění .NET Framework 4.6.2, aplikace spuštěné tímto způsobem už neočekávaně nezmizí – místo toho nebude kontrola pravopisu vypnutá.</span><span class="sxs-lookup"><span data-stu-id="5bdb6-109">Starting .NET Framework 4.6.2, applications launched in this manner will no longer crash unexpectedly - instead the Spell Checker will be silently disabled.</span></span> <span data-ttu-id="5bdb6-110">#3 problému – to bylo opraveno v .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="5bdb6-110">Issue #3 - This has been fixed in .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="5bdb6-111">Name</span><span class="sxs-lookup"><span data-stu-id="5bdb6-111">Name</span></span>    | <span data-ttu-id="5bdb6-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5bdb6-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5bdb6-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="5bdb6-113">Scope</span></span>   |<span data-ttu-id="5bdb6-114">Edge</span><span class="sxs-lookup"><span data-stu-id="5bdb6-114">Edge</span></span>|
|<span data-ttu-id="5bdb6-115">Verze</span><span class="sxs-lookup"><span data-stu-id="5bdb6-115">Version</span></span>|<span data-ttu-id="5bdb6-116">4.6.1</span><span class="sxs-lookup"><span data-stu-id="5bdb6-116">4.6.1</span></span>|
|<span data-ttu-id="5bdb6-117">Typ</span><span class="sxs-lookup"><span data-stu-id="5bdb6-117">Type</span></span>|<span data-ttu-id="5bdb6-118">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="5bdb6-118">Runtime</span></span>|
