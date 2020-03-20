---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804633"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="eb086-101">VB.NET již nepodporuje částečnou kvalifikaci oboru názvů pro systémová api systému.Windows</span><span class="sxs-lookup"><span data-stu-id="eb086-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="eb086-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="eb086-102">Details</span></span>|<span data-ttu-id="eb086-103">Počínaje rozhraním .NET Framework 4.5.2 nelze VB.NET projektů určit rozhraní API systému System.Windows s částečně kvalifikovanými obory názvů.</span><span class="sxs-lookup"><span data-stu-id="eb086-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="eb086-104">Například odkazování <code>Windows.Forms.DialogResult</code> na se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="eb086-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="eb086-105">Místo toho musí kód odkazovat<xref:System.Windows.Forms.DialogResult>na plně kvalifikovaný název ( ) <xref:System.Windows.Forms.DialogResult?displayProperty=name>nebo importovat konkrétní obor názvů a odkazovat jednoduše na .</span><span class="sxs-lookup"><span data-stu-id="eb086-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="eb086-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="eb086-106">Suggestion</span></span>|<span data-ttu-id="eb086-107">Kód by měl být <code>System.Windows</code> aktualizován tak, aby odkazoval na api s jednoduchými názvy (a importem příslušného oboru názvů) nebo s plně kvalifikovanými názvy.</span><span class="sxs-lookup"><span data-stu-id="eb086-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="eb086-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="eb086-108">Scope</span></span>|<span data-ttu-id="eb086-109">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="eb086-109">Minor</span></span>|
|<span data-ttu-id="eb086-110">Version</span><span class="sxs-lookup"><span data-stu-id="eb086-110">Version</span></span>|<span data-ttu-id="eb086-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="eb086-111">4.5.2</span></span>|
|<span data-ttu-id="eb086-112">Typ</span><span class="sxs-lookup"><span data-stu-id="eb086-112">Type</span></span>|<span data-ttu-id="eb086-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="eb086-113">Retargeting</span></span>|
