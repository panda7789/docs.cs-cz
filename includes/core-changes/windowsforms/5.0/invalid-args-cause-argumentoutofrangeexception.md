---
ms.openlocfilehash: f42da00487735acdcc60f876c75e1dfd17103008
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702433"
---
### <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="74e59-101">Vlastnosti WinForms teď vyvolávají výjimku ArgumentOutOfRangeException.</span><span class="sxs-lookup"><span data-stu-id="74e59-101">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="74e59-102">Některé vlastnosti model Windows Forms nyní vyvolají <xref:System.ArgumentOutOfRangeException> neplatných argumentů, kde dříve neexistovaly.</span><span class="sxs-lookup"><span data-stu-id="74e59-102">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="74e59-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="74e59-103">Change description</span></span>

<span data-ttu-id="74e59-104">Dříve tyto vlastnosti vyvolaly různé výjimky, například <xref:System.NullReferenceException> , <xref:System.IndexOutOfRangeException> nebo <xref:System.ArgumentException> , při předání argumentů mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="74e59-104">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="74e59-105">Počínaje rozhraním .NET 5,0 tyto vlastnosti nyní vyvolají <xref:System.ArgumentOutOfRangeException> při předaném argumentech, které jsou mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="74e59-105">Starting in .NET 5.0, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="74e59-106">Vyvolání <xref:System.ArgumentOutOfRangeException> vyhovuje chování modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="74e59-106">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="74e59-107">Vylepšuje také možnosti ladění tím, že jednoznačně komunikuje, který argument je neplatný.</span><span class="sxs-lookup"><span data-stu-id="74e59-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="74e59-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="74e59-108">Version introduced</span></span>

<span data-ttu-id="74e59-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="74e59-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="74e59-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="74e59-110">Recommended action</span></span>

- <span data-ttu-id="74e59-111">Aktualizujte kód, abyste zabránili předávání neplatných argumentů.</span><span class="sxs-lookup"><span data-stu-id="74e59-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="74e59-112">V případě potřeby <xref:System.ArgumentOutOfRangeException> při nastavování vlastnosti zpracujte.</span><span class="sxs-lookup"><span data-stu-id="74e59-112">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

#### <a name="category"></a><span data-ttu-id="74e59-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="74e59-113">Category</span></span>

<span data-ttu-id="74e59-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74e59-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="74e59-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="74e59-115">Affected APIs</span></span>

<span data-ttu-id="74e59-116">Následující tabulka obsahuje seznam ovlivněných vlastností a parametrů:</span><span class="sxs-lookup"><span data-stu-id="74e59-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="74e59-117">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="74e59-117">Property</span></span> | <span data-ttu-id="74e59-118">Název parametru</span><span class="sxs-lookup"><span data-stu-id="74e59-118">Parameter name</span></span> | <span data-ttu-id="74e59-119">Přidaná verze</span><span class="sxs-lookup"><span data-stu-id="74e59-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="74e59-120">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="74e59-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="74e59-121">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="74e59-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="74e59-122">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="74e59-122">5.0 Preview 6</span></span> |

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

-->
