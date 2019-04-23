---
ms.openlocfilehash: de79182e326082786c1e0691f8888e30cd410f5d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235220"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="be50c-101">Výchozí hodnota je textové pole WPF zrušit limit 100</span><span class="sxs-lookup"><span data-stu-id="be50c-101">WPF TextBox defaults to undo limit of 100</span></span>

|   |   |
|---|---|
|<span data-ttu-id="be50c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="be50c-102">Details</span></span>|<span data-ttu-id="be50c-103">Výchozí limit vrácení zpět pro textové pole s WPF v rozhraní .NET Framework 4.5, je 100 (na rozdíl od vrácení neomezený počet v rozhraní .NET Framework 4.0)</span><span class="sxs-lookup"><span data-stu-id="be50c-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>|
|<span data-ttu-id="be50c-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="be50c-104">Suggestion</span></span>|<span data-ttu-id="be50c-105">Pokud zpět maximálně 100 je příliš nízké, limit lze nastavit explicitně pomocí <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span><span class="sxs-lookup"><span data-stu-id="be50c-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>|
|<span data-ttu-id="be50c-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="be50c-106">Scope</span></span>|<span data-ttu-id="be50c-107">Edge</span><span class="sxs-lookup"><span data-stu-id="be50c-107">Edge</span></span>|
|<span data-ttu-id="be50c-108">Version</span><span class="sxs-lookup"><span data-stu-id="be50c-108">Version</span></span>|<span data-ttu-id="be50c-109">4.5</span><span class="sxs-lookup"><span data-stu-id="be50c-109">4.5</span></span>|
|<span data-ttu-id="be50c-110">Type</span><span class="sxs-lookup"><span data-stu-id="be50c-110">Type</span></span>|<span data-ttu-id="be50c-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="be50c-111">Runtime</span></span>|
|<span data-ttu-id="be50c-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="be50c-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
