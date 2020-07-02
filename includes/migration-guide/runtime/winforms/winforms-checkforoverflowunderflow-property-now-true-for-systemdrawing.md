---
ms.openlocfilehash: 4cd06fd02fadbaa9f74e40f850e688ee883454ed
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620090"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="24e58-101">Vlastnost CheckForOverflowUnderflow DataGridView má nyní hodnotu true pro System. Drawing.</span><span class="sxs-lookup"><span data-stu-id="24e58-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

#### <a name="details"></a><span data-ttu-id="24e58-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="24e58-102">Details</span></span>

<span data-ttu-id="24e58-103">Vlastnost CheckForOverflowUnderflow pro sestavení System.Drawing.dll je nastavena na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="24e58-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="24e58-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="24e58-104">Suggestion</span></span>

<span data-ttu-id="24e58-105">Dříve v případě, že dojde k přetečení, by výsledkem bylo tiché zkrácení.</span><span class="sxs-lookup"><span data-stu-id="24e58-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="24e58-106">Nyní <xref:System.OverflowException?displayProperty=fullName> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="24e58-106">Now an <xref:System.OverflowException?displayProperty=fullName> exception is thrown.</span></span>

| <span data-ttu-id="24e58-107">Name</span><span class="sxs-lookup"><span data-stu-id="24e58-107">Name</span></span>    | <span data-ttu-id="24e58-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="24e58-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="24e58-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="24e58-109">Scope</span></span>   |<span data-ttu-id="24e58-110">Edge</span><span class="sxs-lookup"><span data-stu-id="24e58-110">Edge</span></span>|
|<span data-ttu-id="24e58-111">Verze</span><span class="sxs-lookup"><span data-stu-id="24e58-111">Version</span></span>|<span data-ttu-id="24e58-112">4.5</span><span class="sxs-lookup"><span data-stu-id="24e58-112">4.5</span></span>|
|<span data-ttu-id="24e58-113">Typ</span><span class="sxs-lookup"><span data-stu-id="24e58-113">Type</span></span>|<span data-ttu-id="24e58-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="24e58-114">Runtime</span></span>|
