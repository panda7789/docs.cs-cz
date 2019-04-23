---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803719"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="b0845-101">Formuláře Windows na CheckForOverflowUnderflow vlastnost má nyní hodnotu true pro System.Drawing</span><span class="sxs-lookup"><span data-stu-id="b0845-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b0845-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b0845-102">Details</span></span>|<span data-ttu-id="b0845-103">Vlastnost CheckForOverflowUnderflow System.Drawing.dll sestavení je nastavena na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="b0845-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="b0845-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="b0845-104">Suggestion</span></span>|<span data-ttu-id="b0845-105">Dříve v případě, že dojde k přetečení, by výsledkem bylo tiché zkrácení.</span><span class="sxs-lookup"><span data-stu-id="b0845-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="b0845-106">Nyní <xref:System.OverflowException?displayProperty=name> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b0845-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="b0845-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b0845-107">Scope</span></span>|<span data-ttu-id="b0845-108">Edge</span><span class="sxs-lookup"><span data-stu-id="b0845-108">Edge</span></span>|
|<span data-ttu-id="b0845-109">Version</span><span class="sxs-lookup"><span data-stu-id="b0845-109">Version</span></span>|<span data-ttu-id="b0845-110">4.5</span><span class="sxs-lookup"><span data-stu-id="b0845-110">4.5</span></span>|
|<span data-ttu-id="b0845-111">Type</span><span class="sxs-lookup"><span data-stu-id="b0845-111">Type</span></span>|<span data-ttu-id="b0845-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="b0845-112">Runtime</span></span>|
