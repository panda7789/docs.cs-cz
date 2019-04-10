---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235385"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="3cb32-101">Textové pole WPF vybraný text se zobrazí odlišnou barvou, když do textového pole je neaktivní</span><span class="sxs-lookup"><span data-stu-id="3cb32-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3cb32-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3cb32-102">Details</span></span>|<span data-ttu-id="3cb32-103">V rozhraní .NET Framework 4.5, když je neaktivní ovládacího prvku WPF textového pole (nemá fokus), zobrazí se vybraný text v poli jinou barvou, než když je aktivní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="3cb32-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>|
|<span data-ttu-id="3cb32-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="3cb32-104">Suggestion</span></span>|<span data-ttu-id="3cb32-105">Může se obnovit předchozí chování (.NET Framework 4.0) tak, že nastavíte <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> vlastnost <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="3cb32-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>|
|<span data-ttu-id="3cb32-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3cb32-106">Scope</span></span>|<span data-ttu-id="3cb32-107">Edge</span><span class="sxs-lookup"><span data-stu-id="3cb32-107">Edge</span></span>|
|<span data-ttu-id="3cb32-108">Version</span><span class="sxs-lookup"><span data-stu-id="3cb32-108">Version</span></span>|<span data-ttu-id="3cb32-109">4.5</span><span class="sxs-lookup"><span data-stu-id="3cb32-109">4.5</span></span>|
|<span data-ttu-id="3cb32-110">Type</span><span class="sxs-lookup"><span data-stu-id="3cb32-110">Type</span></span>|<span data-ttu-id="3cb32-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="3cb32-111">Runtime</span></span>|
|<span data-ttu-id="3cb32-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3cb32-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
