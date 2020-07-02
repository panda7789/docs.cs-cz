---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621106"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="c7bd5-101">Zřetězené automaticky otevírané okno s nastavením StaysOpen = false</span><span class="sxs-lookup"><span data-stu-id="c7bd5-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="c7bd5-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c7bd5-102">Details</span></span>

<span data-ttu-id="c7bd5-103">Místní nabídka s nastavením StaysOpen = false by se měla zavřít po kliknutí mimo místní nabídku.</span><span class="sxs-lookup"><span data-stu-id="c7bd5-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="c7bd5-104">V případě zřetězení dvou nebo více překryvných oken (tj. jeden obsahuje jiný) existuje mnoho problémů, včetně:</span><span class="sxs-lookup"><span data-stu-id="c7bd5-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="c7bd5-105">Otevřete dvě úrovně, klikněte na mimo P2, ale uvnitř P1.</span><span class="sxs-lookup"><span data-stu-id="c7bd5-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="c7bd5-106">Nic se nestane.</span><span class="sxs-lookup"><span data-stu-id="c7bd5-106">Nothing happens.</span></span></li><li><span data-ttu-id="c7bd5-107">Otevřete dvě úrovně a klikněte mimo P1.</span><span class="sxs-lookup"><span data-stu-id="c7bd5-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="c7bd5-108">Obě automaticky otevíraná okna se zavřou.</span><span class="sxs-lookup"><span data-stu-id="c7bd5-108">Both popups close.</span></span></li><li><span data-ttu-id="c7bd5-109">Otevřete a zavřete dvě úrovně.</span><span class="sxs-lookup"><span data-stu-id="c7bd5-109">Open and close two levels.</span></span>  <span data-ttu-id="c7bd5-110">Pak zkuste znovu otevřít P2.</span><span class="sxs-lookup"><span data-stu-id="c7bd5-110">Then try to open P2 again.</span></span>  <span data-ttu-id="c7bd5-111">Nic se nestane.</span><span class="sxs-lookup"><span data-stu-id="c7bd5-111">Nothing happens.</span></span></li><li><span data-ttu-id="c7bd5-112">Zkuste otevřít tři úrovně.</span><span class="sxs-lookup"><span data-stu-id="c7bd5-112">Try to open three levels.</span></span>  <span data-ttu-id="c7bd5-113">Nemůžete.</span><span class="sxs-lookup"><span data-stu-id="c7bd5-113">You can't.</span></span>  <span data-ttu-id="c7bd5-114">(Buď nic nenastane, nebo první dvě úrovně se zavřou, podle toho, kde kliknete.) Tyto případy (a jiné varianty) teď fungují podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="c7bd5-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="c7bd5-115">Name</span><span class="sxs-lookup"><span data-stu-id="c7bd5-115">Name</span></span>    | <span data-ttu-id="c7bd5-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c7bd5-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c7bd5-117">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c7bd5-117">Scope</span></span>   |<span data-ttu-id="c7bd5-118">Edge</span><span class="sxs-lookup"><span data-stu-id="c7bd5-118">Edge</span></span>|
|<span data-ttu-id="c7bd5-119">Verze</span><span class="sxs-lookup"><span data-stu-id="c7bd5-119">Version</span></span>|<span data-ttu-id="c7bd5-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="c7bd5-120">4.7.1</span></span>|
|<span data-ttu-id="c7bd5-121">Typ</span><span class="sxs-lookup"><span data-stu-id="c7bd5-121">Type</span></span>|<span data-ttu-id="c7bd5-122">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c7bd5-122">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c7bd5-123">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c7bd5-123">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
