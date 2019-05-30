---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379522"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="0c712-101">Textové pole WPF vybraný text se zobrazí odlišnou barvou, když do textového pole je neaktivní</span><span class="sxs-lookup"><span data-stu-id="0c712-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0c712-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0c712-102">Details</span></span>|<span data-ttu-id="0c712-103">V rozhraní .NET Framework 4.5, když je neaktivní ovládacího prvku WPF textového pole (nemá fokus), zobrazí se vybraný text v poli jinou barvou, než když je aktivní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="0c712-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>|
|<span data-ttu-id="0c712-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="0c712-104">Suggestion</span></span>|<span data-ttu-id="0c712-105">Může se obnovit předchozí chování (.NET Framework 4.0) tak, že nastavíte <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> vlastnost <code>false</code>.</span><span class="sxs-lookup"><span data-stu-id="0c712-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>|
|<span data-ttu-id="0c712-106">Scope</span><span class="sxs-lookup"><span data-stu-id="0c712-106">Scope</span></span>|<span data-ttu-id="0c712-107">Edge</span><span class="sxs-lookup"><span data-stu-id="0c712-107">Edge</span></span>|
|<span data-ttu-id="0c712-108">Version</span><span class="sxs-lookup"><span data-stu-id="0c712-108">Version</span></span>|<span data-ttu-id="0c712-109">4.5</span><span class="sxs-lookup"><span data-stu-id="0c712-109">4.5</span></span>|
|<span data-ttu-id="0c712-110">Type</span><span class="sxs-lookup"><span data-stu-id="0c712-110">Type</span></span>|<span data-ttu-id="0c712-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="0c712-111">Runtime</span></span>|
|<span data-ttu-id="0c712-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0c712-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
