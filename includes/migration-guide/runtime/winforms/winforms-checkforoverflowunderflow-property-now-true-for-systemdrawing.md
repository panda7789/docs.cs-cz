---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235283"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="9a1c4-101">Formuláře Windows na CheckForOverflowUnderflow vlastnost má nyní hodnotu true pro System.Drawing</span><span class="sxs-lookup"><span data-stu-id="9a1c4-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9a1c4-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9a1c4-102">Details</span></span>|<span data-ttu-id="9a1c4-103">Vlastnost CheckForOverflowUnderflow System.Drawing.dll sestavení je nastavena na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="9a1c4-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="9a1c4-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="9a1c4-104">Suggestion</span></span>|<span data-ttu-id="9a1c4-105">Dříve v případě, že dojde k přetečení, by výsledkem bylo tiché zkrácení.</span><span class="sxs-lookup"><span data-stu-id="9a1c4-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="9a1c4-106">Nyní <xref:System.OverflowException?displayProperty=name> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9a1c4-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="9a1c4-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="9a1c4-107">Scope</span></span>|<span data-ttu-id="9a1c4-108">Edge</span><span class="sxs-lookup"><span data-stu-id="9a1c4-108">Edge</span></span>|
|<span data-ttu-id="9a1c4-109">Version</span><span class="sxs-lookup"><span data-stu-id="9a1c4-109">Version</span></span>|<span data-ttu-id="9a1c4-110">4.5</span><span class="sxs-lookup"><span data-stu-id="9a1c4-110">4.5</span></span>|
|<span data-ttu-id="9a1c4-111">Type</span><span class="sxs-lookup"><span data-stu-id="9a1c4-111">Type</span></span>|<span data-ttu-id="9a1c4-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="9a1c4-112">Runtime</span></span>|
