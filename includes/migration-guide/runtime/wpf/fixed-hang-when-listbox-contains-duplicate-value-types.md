---
ms.openlocfilehash: 5d5423d18091545ad9d50325900f5a9a4fff6dd9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622017"
---
### <a name="fixed-a-hang-when-listbox-contains-duplicate-value-types"></a><span data-ttu-id="2bfd9-101">Opraveno zablokování, když seznam obsahuje duplicitní typy hodnot</span><span class="sxs-lookup"><span data-stu-id="2bfd9-101">Fixed a hang when ListBox contains duplicate value-types</span></span>

#### <a name="details"></a><span data-ttu-id="2bfd9-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2bfd9-102">Details</span></span>

<span data-ttu-id="2bfd9-103">Opravili jsme problém, kdy virtualizace <xref:System.Windows.Controls.ItemsControl> může během posouvání zareagovat, když kolekce položek obsahuje duplicitní objekty typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2bfd9-103">Fixed a problem where a virtualizing<xref:System.Windows.Controls.ItemsControl> can hang during scrolling when its Items collection contains duplicate value-typed objects.</span></span>

| <span data-ttu-id="2bfd9-104">Name</span><span class="sxs-lookup"><span data-stu-id="2bfd9-104">Name</span></span>    | <span data-ttu-id="2bfd9-105">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2bfd9-105">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2bfd9-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2bfd9-106">Scope</span></span>   |<span data-ttu-id="2bfd9-107">Hlavní</span><span class="sxs-lookup"><span data-stu-id="2bfd9-107">Major</span></span>|
|<span data-ttu-id="2bfd9-108">Verze</span><span class="sxs-lookup"><span data-stu-id="2bfd9-108">Version</span></span>|<span data-ttu-id="2bfd9-109">4,8</span><span class="sxs-lookup"><span data-stu-id="2bfd9-109">4.8</span></span>|
|<span data-ttu-id="2bfd9-110">Typ</span><span class="sxs-lookup"><span data-stu-id="2bfd9-110">Type</span></span>|<span data-ttu-id="2bfd9-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="2bfd9-111">Runtime</span></span>|
