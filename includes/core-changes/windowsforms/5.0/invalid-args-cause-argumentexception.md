---
ms.openlocfilehash: aab7d8538c875e35c832acc2a6c64beb84d4fb47
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702432"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="e0e2d-101">Metody WinForms teď vyvolávají výjimku ArgumentException.</span><span class="sxs-lookup"><span data-stu-id="e0e2d-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="e0e2d-102">Některé metody model Windows Forms nyní vyvolají <xref:System.ArgumentException> neplatných argumentů, kde dříve neexistovaly.</span><span class="sxs-lookup"><span data-stu-id="e0e2d-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e0e2d-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="e0e2d-103">Change description</span></span>

<span data-ttu-id="e0e2d-104">Dřív předávání argumentů neočekávaného nebo nesprávného typu určitým model Windows Forms metodám by způsobilo neurčitý stav.</span><span class="sxs-lookup"><span data-stu-id="e0e2d-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="e0e2d-105">Počínaje rozhraním .NET 5,0 tyto metody nyní vyvolají <xref:System.ArgumentException> při předání neplatných argumentů.</span><span class="sxs-lookup"><span data-stu-id="e0e2d-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="e0e2d-106">Vyvolání <xref:System.ArgumentException> vyhovuje chování modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="e0e2d-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="e0e2d-107">Vylepšuje také možnosti ladění tím, že jednoznačně komunikuje, který argument je neplatný.</span><span class="sxs-lookup"><span data-stu-id="e0e2d-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="e0e2d-108">Následující tabulka uvádí ovlivněné metody a parametry:</span><span class="sxs-lookup"><span data-stu-id="e0e2d-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="e0e2d-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="e0e2d-109">Method</span></span> | <span data-ttu-id="e0e2d-110">Název parametru</span><span class="sxs-lookup"><span data-stu-id="e0e2d-110">Parameter name</span></span> | <span data-ttu-id="e0e2d-111">Podmínka</span><span class="sxs-lookup"><span data-stu-id="e0e2d-111">Condition</span></span> | <span data-ttu-id="e0e2d-112">Přidaná verze</span><span class="sxs-lookup"><span data-stu-id="e0e2d-112">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="e0e2d-113">Argument není typu <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="e0e2d-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="e0e2d-114">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="e0e2d-114">5.0 Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="e0e2d-115">Argument je `null` , <xref:System.String.Empty?displayProperty=nameWithType> nebo mezera.</span><span class="sxs-lookup"><span data-stu-id="e0e2d-115">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="e0e2d-116">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="e0e2d-116">5.0 Preview 5</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="e0e2d-117">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e0e2d-117">Version introduced</span></span>

<span data-ttu-id="e0e2d-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e0e2d-118">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e0e2d-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e0e2d-119">Recommended action</span></span>

- <span data-ttu-id="e0e2d-120">Aktualizujte kód, abyste zabránili předávání neplatných argumentů.</span><span class="sxs-lookup"><span data-stu-id="e0e2d-120">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="e0e2d-121">V případě potřeby zpracujte <xref:System.ArgumentException> při volání metody.</span><span class="sxs-lookup"><span data-stu-id="e0e2d-121">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="e0e2d-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e0e2d-122">Category</span></span>

<span data-ttu-id="e0e2d-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0e2d-123">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e0e2d-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e0e2d-124">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>
- <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`

-->
