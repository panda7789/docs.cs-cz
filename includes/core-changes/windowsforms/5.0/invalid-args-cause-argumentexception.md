---
ms.openlocfilehash: f1fc70075ef09a4f036c69788342c07ee51d72ce
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702483"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="7158d-101">Metody WinForms teď vyvolávají výjimku ArgumentException.</span><span class="sxs-lookup"><span data-stu-id="7158d-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="7158d-102">Některé metody model Windows Forms nyní vyvolají <xref:System.ArgumentException> neplatných argumentů, kde dříve neexistovaly.</span><span class="sxs-lookup"><span data-stu-id="7158d-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7158d-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="7158d-103">Change description</span></span>

<span data-ttu-id="7158d-104">Dřív předávání argumentů neočekávaného nebo nesprávného typu určitým model Windows Forms metodám by způsobilo neurčitý stav.</span><span class="sxs-lookup"><span data-stu-id="7158d-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="7158d-105">Počínaje rozhraním .NET 5,0 tyto metody nyní vyvolají <xref:System.ArgumentException> při předání neplatných argumentů.</span><span class="sxs-lookup"><span data-stu-id="7158d-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="7158d-106">Vyvolání <xref:System.ArgumentException> vyhovuje chování modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="7158d-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="7158d-107">Vylepšuje také možnosti ladění tím, že jednoznačně komunikuje, který argument je neplatný.</span><span class="sxs-lookup"><span data-stu-id="7158d-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="7158d-108">Následující tabulka uvádí ovlivněné metody a parametry:</span><span class="sxs-lookup"><span data-stu-id="7158d-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="7158d-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="7158d-109">Method</span></span> | <span data-ttu-id="7158d-110">Název parametru</span><span class="sxs-lookup"><span data-stu-id="7158d-110">Parameter name</span></span> | <span data-ttu-id="7158d-111">Podmínka</span><span class="sxs-lookup"><span data-stu-id="7158d-111">Condition</span></span> | <span data-ttu-id="7158d-112">Přidaná verze</span><span class="sxs-lookup"><span data-stu-id="7158d-112">Version added</span></span> |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="7158d-113">Argument není typu <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="7158d-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="7158d-114">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="7158d-114">5.0 Preview 1</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="7158d-115">Představená verze</span><span class="sxs-lookup"><span data-stu-id="7158d-115">Version introduced</span></span>

<span data-ttu-id="7158d-116">.NET 5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="7158d-116">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7158d-117">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="7158d-117">Recommended action</span></span>

- <span data-ttu-id="7158d-118">Aktualizujte kód, abyste zabránili předávání neplatných argumentů.</span><span class="sxs-lookup"><span data-stu-id="7158d-118">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="7158d-119">V případě potřeby zpracujte <xref:System.ArgumentException> při volání metody.</span><span class="sxs-lookup"><span data-stu-id="7158d-119">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="7158d-120">Kategorie</span><span class="sxs-lookup"><span data-stu-id="7158d-120">Category</span></span>

<span data-ttu-id="7158d-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7158d-121">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7158d-122">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7158d-122">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
