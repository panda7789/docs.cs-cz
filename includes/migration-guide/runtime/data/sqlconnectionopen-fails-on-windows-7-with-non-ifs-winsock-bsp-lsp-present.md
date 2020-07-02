---
ms.openlocfilehash: a1db9916c69c5974191eb6108fb54a0d9ff060d2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622040"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a><span data-ttu-id="4eaff-101">SqlConnection. Open se nepovedlo ve Windows 7 s neifs Winsock BSP nebo LSP.</span><span class="sxs-lookup"><span data-stu-id="4eaff-101">SqlConnection.Open fails on Windows 7 with non-IFS Winsock BSP or LSP present</span></span>

#### <a name="details"></a><span data-ttu-id="4eaff-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4eaff-102">Details</span></span>

<span data-ttu-id="4eaff-103"><xref:System.Data.SqlClient.SqlConnection.Open>a <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> v počítači se systémem Windows 7 selže v .NET Framework 4,5, pokud je spuštěný počítač se systémem Windows 7, který není IFS Winsock BSP nebo LSP. Chcete-li zjistit, zda je nainstalováno neifs BSP nebo LSP, použijte <code>netsh WinSock Show Catalog</code> příkaz a zkontrolujte všechny <code>Winsock Catalog Provider Entry</code> vrácené položky.</span><span class="sxs-lookup"><span data-stu-id="4eaff-103"><xref:System.Data.SqlClient.SqlConnection.Open> and <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> fail in the .NET Framework 4.5 if running on a Windows 7 machine with a non-IFS Winsock BSP or LSP are present on the computer.To determine whether a non-IFS BSP or LSP is installed, use the <code>netsh WinSock Show Catalog</code> command, and examine every <code>Winsock Catalog Provider Entry</code> item that is returned.</span></span> <span data-ttu-id="4eaff-104">Pokud má hodnota příznaků služby <code>0x20000</code> nastaven bit, zprostředkovatel použije popisovač IFS a bude správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="4eaff-104">If the Service Flags value has the <code>0x20000</code> bit set, the provider uses IFS handles and will work correctly.</span></span> <span data-ttu-id="4eaff-105">Pokud <code>0x20000</code> je bit jasný (nenastavený), jedná se o NEIFS BSP nebo LSP.</span><span class="sxs-lookup"><span data-stu-id="4eaff-105">If the <code>0x20000</code> bit is clear (not set), it is a non-IFS BSP or LSP.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4eaff-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="4eaff-106">Suggestion</span></span>

<span data-ttu-id="4eaff-107">Tato chyba byla opravena v .NET Framework 4.5.2, takže se ji můžete vyhnout upgradem .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4eaff-107">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="4eaff-108">Případně se můžete vyhnout odebráním všech nainstalovaných rozhraní Winsock LSP typu non-IFS.</span><span class="sxs-lookup"><span data-stu-id="4eaff-108">Alternatively, it can be avoided by removing any installed non-IFS Winsock LSPs.</span></span>

| <span data-ttu-id="4eaff-109">Name</span><span class="sxs-lookup"><span data-stu-id="4eaff-109">Name</span></span>    | <span data-ttu-id="4eaff-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4eaff-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4eaff-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4eaff-111">Scope</span></span>   |<span data-ttu-id="4eaff-112">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="4eaff-112">Minor</span></span>|
|<span data-ttu-id="4eaff-113">Verze</span><span class="sxs-lookup"><span data-stu-id="4eaff-113">Version</span></span>|<span data-ttu-id="4eaff-114">4.5</span><span class="sxs-lookup"><span data-stu-id="4eaff-114">4.5</span></span>|
|<span data-ttu-id="4eaff-115">Typ</span><span class="sxs-lookup"><span data-stu-id="4eaff-115">Type</span></span>|<span data-ttu-id="4eaff-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="4eaff-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4eaff-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="4eaff-117">Affected APIs</span></span>

-<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
