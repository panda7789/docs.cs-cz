---
ms.openlocfilehash: cd59818fe674e10a206725bea8a74c4aceed99b1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620098"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="087c8-101">Textové pole WPF – vybraný text se zobrazí v případě neaktivního textového pole s jinou barvou</span><span class="sxs-lookup"><span data-stu-id="087c8-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

#### <a name="details"></a><span data-ttu-id="087c8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="087c8-102">Details</span></span>

<span data-ttu-id="087c8-103">V .NET Framework 4,5, pokud je ovládací prvek textového pole WPF neaktivní (nemá fokus), se vybraný text v poli zobrazí jinou barvou, než je ovládací prvek aktivní.</span><span class="sxs-lookup"><span data-stu-id="087c8-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="087c8-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="087c8-104">Suggestion</span></span>

<span data-ttu-id="087c8-105">Předchozí chování (.NET Framework 4,0) může být obnoveno nastavením <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> vlastnosti na <code>false</code> .</span><span class="sxs-lookup"><span data-stu-id="087c8-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>

| <span data-ttu-id="087c8-106">Name</span><span class="sxs-lookup"><span data-stu-id="087c8-106">Name</span></span>    | <span data-ttu-id="087c8-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="087c8-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="087c8-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="087c8-108">Scope</span></span>   |<span data-ttu-id="087c8-109">Edge</span><span class="sxs-lookup"><span data-stu-id="087c8-109">Edge</span></span>|
|<span data-ttu-id="087c8-110">Verze</span><span class="sxs-lookup"><span data-stu-id="087c8-110">Version</span></span>|<span data-ttu-id="087c8-111">4.5</span><span class="sxs-lookup"><span data-stu-id="087c8-111">4.5</span></span>|
|<span data-ttu-id="087c8-112">Typ</span><span class="sxs-lookup"><span data-stu-id="087c8-112">Type</span></span>|<span data-ttu-id="087c8-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="087c8-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="087c8-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="087c8-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
