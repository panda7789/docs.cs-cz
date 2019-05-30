---
ms.openlocfilehash: 8b2a01eb6dfdd5bd2bcbef6014d4edeb3ec82ac1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379549"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="20cfa-101">Formuláře Windows na CheckForOverflowUnderflow vlastnost má nyní hodnotu true pro System.Drawing</span><span class="sxs-lookup"><span data-stu-id="20cfa-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="20cfa-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="20cfa-102">Details</span></span>|<span data-ttu-id="20cfa-103">Vlastnost CheckForOverflowUnderflow System.Drawing.dll sestavení je nastavena na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="20cfa-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="20cfa-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="20cfa-104">Suggestion</span></span>|<span data-ttu-id="20cfa-105">Dříve v případě, že dojde k přetečení, by výsledkem bylo tiché zkrácení.</span><span class="sxs-lookup"><span data-stu-id="20cfa-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="20cfa-106">Nyní <xref:System.OverflowException?displayProperty=name> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="20cfa-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="20cfa-107">Scope</span><span class="sxs-lookup"><span data-stu-id="20cfa-107">Scope</span></span>|<span data-ttu-id="20cfa-108">Edge</span><span class="sxs-lookup"><span data-stu-id="20cfa-108">Edge</span></span>|
|<span data-ttu-id="20cfa-109">Version</span><span class="sxs-lookup"><span data-stu-id="20cfa-109">Version</span></span>|<span data-ttu-id="20cfa-110">4.5</span><span class="sxs-lookup"><span data-stu-id="20cfa-110">4.5</span></span>|
|<span data-ttu-id="20cfa-111">Type</span><span class="sxs-lookup"><span data-stu-id="20cfa-111">Type</span></span>|<span data-ttu-id="20cfa-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="20cfa-112">Runtime</span></span>|
