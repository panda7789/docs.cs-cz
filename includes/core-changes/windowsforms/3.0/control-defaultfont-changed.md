---
ms.openlocfilehash: 843007ac6467584fbe6350b6ea19ef67609d73e2
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643947"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a><span data-ttu-id="ea37b-101">`Control.DefaultFont` změněn na `Segoe UI 9pt`</span><span class="sxs-lookup"><span data-stu-id="ea37b-101">`Control.DefaultFont` changed to `Segoe UI 9pt`</span></span>

#### <a name="change-description"></a><span data-ttu-id="ea37b-102">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="ea37b-102">Change description</span></span>

<span data-ttu-id="ea37b-103">V .NET Framework byla vlastnost <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> nastavena na `Microsoft Sans Serif 8pt`.</span><span class="sxs-lookup"><span data-stu-id="ea37b-103">In the .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="ea37b-104">Následující obrázek ukazuje okno, které používá výchozí písmo.</span><span class="sxs-lookup"><span data-stu-id="ea37b-104">The following figure shows a window that uses the default font.</span></span>

![výchozí písmo ovládacího prvku v .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="ea37b-106">V .NET Core Počínaje rozhraním .NET Core 3,0 je nastavená na `Segoe UI 9pt` (stejné písmo jako <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="ea37b-106">In .NET Core starting with .NET Core 3.0, it is set to `Segoe UI 9pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="ea37b-107">V důsledku této změny budou mít formuláře a ovládací prvky velikost přibližně 27% větší, než je výsledkem větší velikost nového výchozího písma.</span><span class="sxs-lookup"><span data-stu-id="ea37b-107">As a result of this change, forms and controls will be sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="ea37b-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ea37b-108">For example:</span></span>

![výchozí ovládací prvek Font-in .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="ea37b-110">Tato změna byla provedena v souladu s [pokyny pro uživatelské rozhraní Windows](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span><span class="sxs-lookup"><span data-stu-id="ea37b-110">This change was made to align with [Windows UX guidelines](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ea37b-111">Představená verze</span><span class="sxs-lookup"><span data-stu-id="ea37b-111">Version introduced</span></span>

<span data-ttu-id="ea37b-112">3,0</span><span class="sxs-lookup"><span data-stu-id="ea37b-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ea37b-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="ea37b-113">Recommended action</span></span>

<span data-ttu-id="ea37b-114">Kvůli změně velikosti formulářů a ovládacích prvků se ujistěte, že se vaše aplikace vykresluje správně.</span><span class="sxs-lookup"><span data-stu-id="ea37b-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="ea37b-115">Chcete-li zachovat původní písmo, nastavte výchozí písmo formuláře na `Microsoft Sans Serif 8pt`.</span><span class="sxs-lookup"><span data-stu-id="ea37b-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="ea37b-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ea37b-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="ea37b-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="ea37b-117">Category</span></span>

- <span data-ttu-id="ea37b-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ea37b-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ea37b-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ea37b-119">Affected APIs</span></span>

<span data-ttu-id="ea37b-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="ea37b-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
