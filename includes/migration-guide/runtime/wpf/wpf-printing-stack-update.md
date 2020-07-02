---
ms.openlocfilehash: 5e2e8d1ec5d698d1c1649c2a0a1b4b77dbdf4022
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621118"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="969d9-101">Aktualizace zásobníku pro tisk WPF</span><span class="sxs-lookup"><span data-stu-id="969d9-101">WPF Printing Stack Update</span></span>

#### <a name="details"></a><span data-ttu-id="969d9-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="969d9-102">Details</span></span>

<span data-ttu-id="969d9-103">Rozhraní API pro tisk v GRAFICKÉm rozhraní <xref:System.Printing.PrintQueue?displayProperty=fullName> API pomocí okna pro tisk balíčku.</span><span class="sxs-lookup"><span data-stu-id="969d9-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=fullName> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="969d9-104">Tato změna se provedla s ohledem na službu. žádný z uživatelů ani vývojářů by neměl zobrazovat žádné změny v chování nebo použití rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="969d9-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="969d9-105">Při spuštění ve Windows 10 Creators Update je nový tiskový zásobník standardně povolený.</span><span class="sxs-lookup"><span data-stu-id="969d9-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="969d9-106">Starý tiskový zásobník bude dál fungovat stejně jako dřív ve starších verzích Windows.</span><span class="sxs-lookup"><span data-stu-id="969d9-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="969d9-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="969d9-107">Suggestion</span></span>

<span data-ttu-id="969d9-108">Pokud chcete použít starou sadu Windows 10 Creators Update, nastavte <code>UseXpsOMPrinting</code> REG_DWORD hodnotu <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> klíče registru na <code>1</code> .</span><span class="sxs-lookup"><span data-stu-id="969d9-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>

| <span data-ttu-id="969d9-109">Name</span><span class="sxs-lookup"><span data-stu-id="969d9-109">Name</span></span>    | <span data-ttu-id="969d9-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="969d9-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="969d9-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="969d9-111">Scope</span></span>   |<span data-ttu-id="969d9-112">Edge</span><span class="sxs-lookup"><span data-stu-id="969d9-112">Edge</span></span>|
|<span data-ttu-id="969d9-113">Verze</span><span class="sxs-lookup"><span data-stu-id="969d9-113">Version</span></span>|<span data-ttu-id="969d9-114">4,7</span><span class="sxs-lookup"><span data-stu-id="969d9-114">4.7</span></span>|
|<span data-ttu-id="969d9-115">Typ</span><span class="sxs-lookup"><span data-stu-id="969d9-115">Type</span></span>|<span data-ttu-id="969d9-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="969d9-116">Runtime</span></span>|
