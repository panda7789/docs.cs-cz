---
ms.openlocfilehash: de79182e326082786c1e0691f8888e30cd410f5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235220"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="bd9be-101">Výchozí hodnota je textové pole WPF zrušit limit 100</span><span class="sxs-lookup"><span data-stu-id="bd9be-101">WPF TextBox defaults to undo limit of 100</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bd9be-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bd9be-102">Details</span></span>|<span data-ttu-id="bd9be-103">Výchozí limit vrácení zpět pro textové pole s WPF v rozhraní .NET Framework 4.5, je 100 (na rozdíl od vrácení neomezený počet v rozhraní .NET Framework 4.0)</span><span class="sxs-lookup"><span data-stu-id="bd9be-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>|
|<span data-ttu-id="bd9be-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="bd9be-104">Suggestion</span></span>|<span data-ttu-id="bd9be-105">Pokud zpět maximálně 100 je příliš nízké, limit lze nastavit explicitně pomocí</span><span class="sxs-lookup"><span data-stu-id="bd9be-105">If an undo limit of 100 is too low, the limit can be set explicitly with</span></span> <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>|
|<span data-ttu-id="bd9be-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="bd9be-106">Scope</span></span>|<span data-ttu-id="bd9be-107">Edge</span><span class="sxs-lookup"><span data-stu-id="bd9be-107">Edge</span></span>|
|<span data-ttu-id="bd9be-108">Version</span><span class="sxs-lookup"><span data-stu-id="bd9be-108">Version</span></span>|<span data-ttu-id="bd9be-109">4.5</span><span class="sxs-lookup"><span data-stu-id="bd9be-109">4.5</span></span>|
|<span data-ttu-id="bd9be-110">Type</span><span class="sxs-lookup"><span data-stu-id="bd9be-110">Type</span></span>|<span data-ttu-id="bd9be-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="bd9be-111">Runtime</span></span>|
|<span data-ttu-id="bd9be-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bd9be-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
