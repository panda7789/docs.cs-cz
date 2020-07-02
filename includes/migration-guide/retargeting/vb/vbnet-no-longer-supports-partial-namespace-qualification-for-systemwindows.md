---
ms.openlocfilehash: cef8096c971da8ae245ff974697022f350cb9195
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616041"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="33f1e-101">VB.NET už nepodporuje částečnou kvalifikaci oboru názvů pro System. rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="33f1e-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

#### <a name="details"></a><span data-ttu-id="33f1e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="33f1e-102">Details</span></span>

<span data-ttu-id="33f1e-103">Počínaje .NET Framework 4.5.2 nemohou projekty VB.NET určovat rozhraní API System. Windows s částečně kvalifikovanými obory názvů.</span><span class="sxs-lookup"><span data-stu-id="33f1e-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="33f1e-104">Například odkaz na se `Windows.Forms.DialogResult` nezdaří.</span><span class="sxs-lookup"><span data-stu-id="33f1e-104">For example, referring to `Windows.Forms.DialogResult` will fail.</span></span> <span data-ttu-id="33f1e-105">Místo toho musí kód odkazovat na plně kvalifikovaný název ( <xref:System.Windows.Forms.DialogResult> ) nebo importovat konkrétní obor názvů a odkazovat pouze na <xref:System.Windows.Forms.DialogResult?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="33f1e-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="33f1e-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="33f1e-106">Suggestion</span></span>

<span data-ttu-id="33f1e-107">Kód by měl být aktualizován, aby odkazoval na `System.Windows` rozhraní API buď pomocí jednoduchých názvů (a importu příslušného oboru názvů), nebo s plně kvalifikovanými názvy.</span><span class="sxs-lookup"><span data-stu-id="33f1e-107">Code should be updated to refer to `System.Windows` APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>

| <span data-ttu-id="33f1e-108">Name</span><span class="sxs-lookup"><span data-stu-id="33f1e-108">Name</span></span>    | <span data-ttu-id="33f1e-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="33f1e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="33f1e-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="33f1e-110">Scope</span></span>   | <span data-ttu-id="33f1e-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="33f1e-111">Minor</span></span>       |
| <span data-ttu-id="33f1e-112">Verze</span><span class="sxs-lookup"><span data-stu-id="33f1e-112">Version</span></span> | <span data-ttu-id="33f1e-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="33f1e-113">4.5.2</span></span>       |
| <span data-ttu-id="33f1e-114">Typ</span><span class="sxs-lookup"><span data-stu-id="33f1e-114">Type</span></span>    | <span data-ttu-id="33f1e-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="33f1e-115">Retargeting</span></span> |
