---
ms.openlocfilehash: 9f6703c77e17ac9376aee944b891f4635dc7632e
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309137"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="05660-101">Metody WinForms teď vyvolávají výjimku ArgumentException.</span><span class="sxs-lookup"><span data-stu-id="05660-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="05660-102">Některé metody model Windows Forms nyní vyvolají <xref:System.ArgumentException> neplatných argumentů, kde dříve neexistovaly.</span><span class="sxs-lookup"><span data-stu-id="05660-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="05660-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="05660-103">Change description</span></span>

<span data-ttu-id="05660-104">Dřív předávání argumentů neočekávaného nebo nesprávného typu určitým model Windows Forms metodám by způsobilo neurčitý stav.</span><span class="sxs-lookup"><span data-stu-id="05660-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="05660-105">Počínaje rozhraním .NET 5,0 tyto metody nyní vyvolají <xref:System.ArgumentException> při předání neplatných argumentů.</span><span class="sxs-lookup"><span data-stu-id="05660-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="05660-106">Vyvolání <xref:System.ArgumentException> vyhovuje chování modulu runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="05660-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="05660-107">Vylepšuje také možnosti ladění tím, že jednoznačně komunikuje, který argument je neplatný.</span><span class="sxs-lookup"><span data-stu-id="05660-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="05660-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="05660-108">Version introduced</span></span>

<span data-ttu-id="05660-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="05660-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="05660-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="05660-110">Recommended action</span></span>

- <span data-ttu-id="05660-111">Aktualizujte kód, abyste zabránili předávání neplatných argumentů.</span><span class="sxs-lookup"><span data-stu-id="05660-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="05660-112">V případě potřeby zpracujte <xref:System.ArgumentException> při volání metody.</span><span class="sxs-lookup"><span data-stu-id="05660-112">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="05660-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="05660-113">Category</span></span>

<span data-ttu-id="05660-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05660-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="05660-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="05660-115">Affected APIs</span></span>

<span data-ttu-id="05660-116">Následující tabulka uvádí ovlivněné metody a parametry:</span><span class="sxs-lookup"><span data-stu-id="05660-116">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="05660-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="05660-117">Method</span></span> | <span data-ttu-id="05660-118">Název parametru</span><span class="sxs-lookup"><span data-stu-id="05660-118">Parameter name</span></span> | <span data-ttu-id="05660-119">Stav</span><span class="sxs-lookup"><span data-stu-id="05660-119">Condition</span></span> | <span data-ttu-id="05660-120">Přidaná verze</span><span class="sxs-lookup"><span data-stu-id="05660-120">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="05660-121">Argument není typu <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="05660-121">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="05660-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="05660-122">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="05660-123">Argument je `null` , <xref:System.String.Empty?displayProperty=nameWithType> nebo mezera.</span><span class="sxs-lookup"><span data-stu-id="05660-123">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="05660-124">Preview 5</span><span class="sxs-lookup"><span data-stu-id="05660-124">Preview 5</span></span> |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | <span data-ttu-id="05660-125">Nelze načíst `InputLanguage` pro určenou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="05660-125">Unable to retrieve an `InputLanguage` for the specified culture.</span></span> | <span data-ttu-id="05660-126">Preview 7</span><span class="sxs-lookup"><span data-stu-id="05660-126">Preview 7</span></span> |

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

-->
