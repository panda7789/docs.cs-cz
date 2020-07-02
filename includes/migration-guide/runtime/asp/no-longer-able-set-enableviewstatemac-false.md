---
ms.openlocfilehash: cecb7b2abd4f57fdaacb0ea373cc19dc3cd9b24a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619936"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="6de81-101">Už není možné nastavit EnableViewStateMac na false.</span><span class="sxs-lookup"><span data-stu-id="6de81-101">No longer able to set EnableViewStateMac to false</span></span>

#### <a name="details"></a><span data-ttu-id="6de81-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6de81-102">Details</span></span>

<span data-ttu-id="6de81-103">ASP.NET už neumožňuje vývojářům zadat <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> nebo <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code> .</span><span class="sxs-lookup"><span data-stu-id="6de81-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="6de81-104">Pro všechny požadavky se stavem vloženého zobrazení je nyní vynutil ověřovací kód zprávy o stavu zobrazení (MAC).</span><span class="sxs-lookup"><span data-stu-id="6de81-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="6de81-105">Ovlivněny jsou pouze aplikace, které explicitně nastavily vlastnost EnableViewStateMac <code>false</code> .</span><span class="sxs-lookup"><span data-stu-id="6de81-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6de81-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="6de81-106">Suggestion</span></span>

<span data-ttu-id="6de81-107">EnableViewStateMac se musí předpokládat, že má hodnotu true, a všechny výsledné chyby MAC musí být vyřešené (jak je vysvětleno v [těchto pokynech](https://support.microsoft.com/kb/2915218), které obsahují více rozlišení v závislosti na konkrétních hodnotách, které způsobují chyby Mac).</span><span class="sxs-lookup"><span data-stu-id="6de81-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>

| <span data-ttu-id="6de81-108">Name</span><span class="sxs-lookup"><span data-stu-id="6de81-108">Name</span></span>    | <span data-ttu-id="6de81-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6de81-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6de81-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="6de81-110">Scope</span></span>   |<span data-ttu-id="6de81-111">Hlavní</span><span class="sxs-lookup"><span data-stu-id="6de81-111">Major</span></span>|
|<span data-ttu-id="6de81-112">Verze</span><span class="sxs-lookup"><span data-stu-id="6de81-112">Version</span></span>|<span data-ttu-id="6de81-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="6de81-113">4.5.2</span></span>|
|<span data-ttu-id="6de81-114">Typ</span><span class="sxs-lookup"><span data-stu-id="6de81-114">Type</span></span>|<span data-ttu-id="6de81-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="6de81-115">Runtime</span></span>|
