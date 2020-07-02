---
ms.openlocfilehash: 2aa6603e2ed77ffa94fbc6325cd5db50985bda6a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620080"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a><span data-ttu-id="03667-101">PreviewLostKeyboardFocus se volá opakovaně, pokud jeho obslužná rutina zobrazuje okno se zprávou model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="03667-101">PreviewLostKeyboardFocus is called repeatedly if its handler shows a Windows Forms message box</span></span>

#### <a name="details"></a><span data-ttu-id="03667-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="03667-102">Details</span></span>

<span data-ttu-id="03667-103">Počínaje .NET Framework 4,5, volání <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> z <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> obslužné rutiny způsobí, že se obslužná rutina znovu aktivuje při zavření okna se zprávou, což může vést k nekonečné smyčce oken se zprávami.</span><span class="sxs-lookup"><span data-stu-id="03667-103">Beginning in the .NET Framework 4.5, calling <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> from a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> handler will cause the handler to re-fire when the message box is closed, potentially resulting in an infinite loop of message boxes.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="03667-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="03667-104">Suggestion</span></span>

<span data-ttu-id="03667-105">Tento problém můžete vyřešit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="03667-105">There are two options to work around this issue:</span></span><ol><li><span data-ttu-id="03667-106">Je možné se vyhnout voláním <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> místo <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="03667-106">It may be avoided by calling <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> instead of <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span></span></li><li><span data-ttu-id="03667-107">Je možné se vyhnout zobrazením okna se zprávou z <xref:System.Windows.UIElement.LostKeyboardFocus> obslužné rutiny události (na rozdíl od <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> obslužné rutiny události).</span><span class="sxs-lookup"><span data-stu-id="03667-107">It may be avoided by showing the message box from a <xref:System.Windows.UIElement.LostKeyboardFocus> event handler (as opposed to a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> event handler).</span></span></li></ol>

| <span data-ttu-id="03667-108">Name</span><span class="sxs-lookup"><span data-stu-id="03667-108">Name</span></span>    | <span data-ttu-id="03667-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="03667-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="03667-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="03667-110">Scope</span></span>   |<span data-ttu-id="03667-111">Edge</span><span class="sxs-lookup"><span data-stu-id="03667-111">Edge</span></span>|
|<span data-ttu-id="03667-112">Verze</span><span class="sxs-lookup"><span data-stu-id="03667-112">Version</span></span>|<span data-ttu-id="03667-113">4.5</span><span class="sxs-lookup"><span data-stu-id="03667-113">4.5</span></span>|
|<span data-ttu-id="03667-114">Typ</span><span class="sxs-lookup"><span data-stu-id="03667-114">Type</span></span>|<span data-ttu-id="03667-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="03667-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="03667-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="03667-116">Affected APIs</span></span>

-<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
