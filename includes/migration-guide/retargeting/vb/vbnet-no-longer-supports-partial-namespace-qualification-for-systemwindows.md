---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236735"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="88a00-101">VB.NET už nepodporuje kvalifikace částečné obor názvů System.Windows rozhraní API</span><span class="sxs-lookup"><span data-stu-id="88a00-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="88a00-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="88a00-102">Details</span></span>|<span data-ttu-id="88a00-103">Počínaje .NET Framework 4.5.2, VB.NET projekty nelze zadat System.Windows rozhraní API s částečně kvalifikované obory názvů.</span><span class="sxs-lookup"><span data-stu-id="88a00-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="88a00-104">Například odkazující na <code>Windows.Forms.DialogResult</code> se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="88a00-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="88a00-105">Místo toho kód musí odkazovat na plně kvalifikovaný název (<xref:System.Windows.Forms.DialogResult>) nebo importovat konkrétní obor názvů a odkazovat pouze na <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="88a00-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="88a00-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="88a00-106">Suggestion</span></span>|<span data-ttu-id="88a00-107">Kód by měl aktualizovat o <code>System.Windows</code> rozhraní API pomocí jednoduchých názvy (a import oboru názvů relevantní) nebo s plně kvalifikované názvy.</span><span class="sxs-lookup"><span data-stu-id="88a00-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="88a00-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="88a00-108">Scope</span></span>|<span data-ttu-id="88a00-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="88a00-109">Minor</span></span>|
|<span data-ttu-id="88a00-110">Version</span><span class="sxs-lookup"><span data-stu-id="88a00-110">Version</span></span>|<span data-ttu-id="88a00-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="88a00-111">4.5.2</span></span>|
|<span data-ttu-id="88a00-112">Type</span><span class="sxs-lookup"><span data-stu-id="88a00-112">Type</span></span>|<span data-ttu-id="88a00-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="88a00-113">Retargeting</span></span>|
