---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936993"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a><span data-ttu-id="a2f84-101">Výchozí písmo ovládacího prvku se změnilo na Segoe UI 9 bodů.</span><span class="sxs-lookup"><span data-stu-id="a2f84-101">Default control font changed to Segoe UI 9 pt</span></span>

#### <a name="change-description"></a><span data-ttu-id="a2f84-102">Popis změny</span><span class="sxs-lookup"><span data-stu-id="a2f84-102">Change description</span></span>

<span data-ttu-id="a2f84-103">V .NET Framework byla vlastnost <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> nastavena na `Microsoft Sans Serif 8 pt`.</span><span class="sxs-lookup"><span data-stu-id="a2f84-103">In .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="a2f84-104">Následující obrázek ukazuje okno, které používá výchozí písmo.</span><span class="sxs-lookup"><span data-stu-id="a2f84-104">The following image shows a window that uses the default font.</span></span>

![Výchozí písmo ovládacího prvku v .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="a2f84-106">Počínaje platformou .NET Core 3,0 je výchozí písmo nastavené na `Segoe UI 9 pt` (stejné písmo jako <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="a2f84-106">Starting in .NET Core 3.0, the default font is set to `Segoe UI 9 pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="a2f84-107">V důsledku této změny mají formuláře a ovládací prvky velikost přibližně 27% větší, než je větší velikost nového výchozího písma.</span><span class="sxs-lookup"><span data-stu-id="a2f84-107">As a result of this change, forms and controls are sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="a2f84-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a2f84-108">For example:</span></span>

![Výchozí písmo ovládacího prvku v .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="a2f84-110">Tato změna byla provedena v souladu s [pokyny pro uživatelské prostředí systému Windows (UX)](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span><span class="sxs-lookup"><span data-stu-id="a2f84-110">This change was made to align with [Windows user experience (UX) guidelines](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a2f84-111">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a2f84-111">Version introduced</span></span>

<span data-ttu-id="a2f84-112">3,0</span><span class="sxs-lookup"><span data-stu-id="a2f84-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a2f84-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a2f84-113">Recommended action</span></span>

<span data-ttu-id="a2f84-114">Kvůli změně velikosti formulářů a ovládacích prvků se ujistěte, že se vaše aplikace vykresluje správně.</span><span class="sxs-lookup"><span data-stu-id="a2f84-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="a2f84-115">Chcete-li zachovat původní písmo, nastavte výchozí písmo formuláře na `Microsoft Sans Serif 8 pt`.</span><span class="sxs-lookup"><span data-stu-id="a2f84-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="a2f84-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a2f84-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="a2f84-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a2f84-117">Category</span></span>

- <span data-ttu-id="a2f84-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a2f84-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a2f84-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a2f84-119">Affected APIs</span></span>

<span data-ttu-id="a2f84-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="a2f84-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
