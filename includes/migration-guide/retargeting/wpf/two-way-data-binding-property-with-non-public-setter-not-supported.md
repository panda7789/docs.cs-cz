---
ms.openlocfilehash: 5f1a8af37a305ab0904801002dd99e17e8eca62e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616048"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a><span data-ttu-id="77b62-101">Obousměrná datová vazba na vlastnost s neveřejnou metodou Setter není podporovaná.</span><span class="sxs-lookup"><span data-stu-id="77b62-101">Two-way data-binding to a property with a non-public setter is not supported</span></span>

#### <a name="details"></a><span data-ttu-id="77b62-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="77b62-102">Details</span></span>

<span data-ttu-id="77b62-103">Při pokusu o vytvoření vazby dat na vlastnost bez veřejné metody setter nebyl nikdy podporován scénář.</span><span class="sxs-lookup"><span data-stu-id="77b62-103">Attempting to data bind to a property without a public setter has never been a supported scenario.</span></span> <span data-ttu-id="77b62-104">Počínaje .NET Framework 4.5.1 Tento scénář vyvolá <xref:System.InvalidOperationException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="77b62-104">Beginning in the .NET Framework 4.5.1, this scenario will throw an <xref:System.InvalidOperationException?displayProperty=fullName>.</span></span> <span data-ttu-id="77b62-105">Všimněte si, že tato nová výjimka bude vyvolána jenom pro aplikace, které specificky cílí na .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="77b62-105">Note that this new exception will only be thrown for apps that specifically target the .NET Framework 4.5.1.</span></span> <span data-ttu-id="77b62-106">Pokud je aplikace cílena na .NET Framework 4,5, volání bude povoleno.</span><span class="sxs-lookup"><span data-stu-id="77b62-106">If an app targets the .NET Framework 4.5, the call will be allowed.</span></span> <span data-ttu-id="77b62-107">Pokud aplikace necílí na konkrétní verzi .NET Framework, vazba bude považována za jednosměrnou.</span><span class="sxs-lookup"><span data-stu-id="77b62-107">If the app does not target a particular .NET Framework version, the binding will be treated as one-way.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="77b62-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="77b62-108">Suggestion</span></span>

<span data-ttu-id="77b62-109">Aplikace by se měla aktualizovat tak, aby buď používala jednosměrnou vazbu, nebo veřejně vystavovat metodu setter vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="77b62-109">The app should be updated to either use one-way binding, or expose the property's setter publicly.</span></span> <span data-ttu-id="77b62-110">Případně cílení na .NET Framework 4,5 způsobí, že aplikace vykazuje původní chování.</span><span class="sxs-lookup"><span data-stu-id="77b62-110">Alternatively, targeting the .NET Framework 4.5 will cause the app to exhibit the old behavior.</span></span>

| <span data-ttu-id="77b62-111">Name</span><span class="sxs-lookup"><span data-stu-id="77b62-111">Name</span></span>    | <span data-ttu-id="77b62-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="77b62-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="77b62-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="77b62-113">Scope</span></span>   | <span data-ttu-id="77b62-114">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="77b62-114">Minor</span></span>       |
| <span data-ttu-id="77b62-115">Verze</span><span class="sxs-lookup"><span data-stu-id="77b62-115">Version</span></span> | <span data-ttu-id="77b62-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="77b62-116">4.5.1</span></span>       |
| <span data-ttu-id="77b62-117">Typ</span><span class="sxs-lookup"><span data-stu-id="77b62-117">Type</span></span>    | <span data-ttu-id="77b62-118">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="77b62-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="77b62-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="77b62-119">Affected APIs</span></span>

- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>
