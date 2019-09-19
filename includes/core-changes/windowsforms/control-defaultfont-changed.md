---
ms.openlocfilehash: 02dbf5ccca97f5e7d2e1fada39bdf601cf37906f
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119357"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a><span data-ttu-id="632a0-101">`Control.DefaultFont`změněno na`Segoe UI 9pt`</span><span class="sxs-lookup"><span data-stu-id="632a0-101">`Control.DefaultFont` changed to `Segoe UI 9pt`</span></span> 

#### <a name="change-description"></a><span data-ttu-id="632a0-102">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="632a0-102">Change description</span></span>

<span data-ttu-id="632a0-103">V .NET Framework <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> byla vlastnost nastavena na `Microsoft Sans Serif 8pt`.</span><span class="sxs-lookup"><span data-stu-id="632a0-103">In the .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="632a0-104">Následující obrázek ukazuje okno, které používá výchozí písmo.</span><span class="sxs-lookup"><span data-stu-id="632a0-104">The following figure shows a window that uses the default font.</span></span>

![výchozí písmo ovládacího prvku v .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="632a0-106">V .NET Core Počínaje rozhraním .NET Core 3,0 je nastavená na `Segoe UI 9pt` (stejné písmo jako <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="632a0-106">In .NET Core starting with .NET Core 3.0, it is set to `Segoe UI 9pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="632a0-107">V důsledku této změny budou mít formuláře a ovládací prvky velikost přibližně 27% větší, než je výsledkem větší velikost nového výchozího písma.</span><span class="sxs-lookup"><span data-stu-id="632a0-107">As a result of this change, forms and controls will be sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="632a0-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="632a0-108">For example:</span></span>

![výchozí ovládací prvek Font-in .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="632a0-110">Tato změna byla provedena v souladu s [pokyny pro uživatelské rozhraní Windows](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span><span class="sxs-lookup"><span data-stu-id="632a0-110">This change was made to align with [Windows UX guidelines](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="632a0-111">Představená verze</span><span class="sxs-lookup"><span data-stu-id="632a0-111">Version introduced</span></span>

<span data-ttu-id="632a0-112">3.0</span><span class="sxs-lookup"><span data-stu-id="632a0-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="632a0-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="632a0-113">Recommended action</span></span>

<span data-ttu-id="632a0-114">Kvůli změně velikosti formulářů a ovládacích prvků se ujistěte, že se vaše aplikace vykresluje správně.</span><span class="sxs-lookup"><span data-stu-id="632a0-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="632a0-115">Chcete-li zachovat původní písmo, nastavte výchozí písmo formuláře na `Microsoft Sans Serif 8pt`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="632a0-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="632a0-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="632a0-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="632a0-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="632a0-117">Category</span></span>

- <span data-ttu-id="632a0-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="632a0-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="632a0-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="632a0-119">Affected APIs</span></span>

<span data-ttu-id="632a0-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="632a0-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->