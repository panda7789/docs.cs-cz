---
ms.openlocfilehash: b92dc8a1c48e83846c3d9a1d86e66629f31b7722
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622018"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a><span data-ttu-id="38245-101">Při použití vlastních šablon DataTemplates se občas nedá přejít na spodní položku v ItemsControls (například ListBox a DataGrid).</span><span class="sxs-lookup"><span data-stu-id="38245-101">Intermittently unable to scroll to bottom item in ItemsControls (like ListBox and DataGrid) when using custom DataTemplates</span></span>

#### <a name="details"></a><span data-ttu-id="38245-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="38245-102">Details</span></span>

<span data-ttu-id="38245-103">V některých případech chyby v .NET Framework 4,5 způsobují ItemsControls (například <xref:System.Windows.Controls.ListBox?displayProperty=fullName> , <xref:System.Windows.Controls.ComboBox?displayProperty=fullName> , atd <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> .), aby se při použití vlastních šablon DataTemplate nepřesunuly na jejich spodní položku.</span><span class="sxs-lookup"><span data-stu-id="38245-103">In some instances, a bug in the .NET Framework 4.5 is causing ItemsControls (like <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, <xref:System.Windows.Controls.ComboBox?displayProperty=fullName>, <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>, etc.) to not scroll to their bottom item when using custom DataTemplates.</span></span> <span data-ttu-id="38245-104">Pokud se pokusy o posouvání podruhé (po posunu nahoru), budou fungovat.</span><span class="sxs-lookup"><span data-stu-id="38245-104">If the scrolling is attempted a second time (after scrolling back up), it will work then.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="38245-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="38245-105">Suggestion</span></span>

<span data-ttu-id="38245-106">Tento problém byl opraven v .NET Framework 4.5.2 a může se řešit upgradem na tuto verzi (nebo novější verzi) .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="38245-106">This issue has been fixed in the .NET Framework 4.5.2 and may be addressed by upgrading to that version (or a later version) of the .NET Framework.</span></span> <span data-ttu-id="38245-107">Další možností je, že uživatelé stále mohou přesouvat posuvníky do konečných položek v těchto kolekcích, ale může se to pokusit provést dvakrát, aby to bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="38245-107">Alternatively, users can still drag scroll bars to the final items in these collections, but may need to try twice to do so successfully.</span></span>

| <span data-ttu-id="38245-108">Name</span><span class="sxs-lookup"><span data-stu-id="38245-108">Name</span></span>    | <span data-ttu-id="38245-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="38245-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="38245-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="38245-110">Scope</span></span>   |<span data-ttu-id="38245-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="38245-111">Minor</span></span>|
|<span data-ttu-id="38245-112">Verze</span><span class="sxs-lookup"><span data-stu-id="38245-112">Version</span></span>|<span data-ttu-id="38245-113">4.5</span><span class="sxs-lookup"><span data-stu-id="38245-113">4.5</span></span>|
|<span data-ttu-id="38245-114">Typ</span><span class="sxs-lookup"><span data-stu-id="38245-114">Type</span></span>|<span data-ttu-id="38245-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="38245-115">Runtime</span></span>|
