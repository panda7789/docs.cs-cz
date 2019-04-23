---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118471"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="49da2-101">Už nebude moct EnableViewStateMac nastavena na hodnotu false</span><span class="sxs-lookup"><span data-stu-id="49da2-101">No longer able to set EnableViewStateMac to false</span></span>

|   |   |
|---|---|
|<span data-ttu-id="49da2-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="49da2-102">Details</span></span>|<span data-ttu-id="49da2-103">ASP.NET už umožňuje vývojářům zadat <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> nebo <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="49da2-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="49da2-104">V zobrazení stavu ověřovací kód zprávy (MAC) je nyní vynucena pro všechny požadavky se stavem vložené zobrazení.</span><span class="sxs-lookup"><span data-stu-id="49da2-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="49da2-105">Jenom aplikace, které explicitně nastavit vlastnost EnableViewStateMac na <code>false</code> se to týká.</span><span class="sxs-lookup"><span data-stu-id="49da2-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>|
|<span data-ttu-id="49da2-106">Doporučení</span><span class="sxs-lookup"><span data-stu-id="49da2-106">Suggestion</span></span>|<span data-ttu-id="49da2-107">EnableViewStateMac musí být předpokládá, že na hodnotu true, a všechny případné chyby MAC musí být vyřešeny (jak je vysvětleno v [tyto pokyny](https://support.microsoft.com/kb/2915218), která obsahuje řešení více rozlišení v závislosti na tom, jaké jsou specifikace co je příčinou chyb MAC).</span><span class="sxs-lookup"><span data-stu-id="49da2-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>|
|<span data-ttu-id="49da2-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="49da2-108">Scope</span></span>|<span data-ttu-id="49da2-109">Hlavní</span><span class="sxs-lookup"><span data-stu-id="49da2-109">Major</span></span>|
|<span data-ttu-id="49da2-110">Version</span><span class="sxs-lookup"><span data-stu-id="49da2-110">Version</span></span>|<span data-ttu-id="49da2-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="49da2-111">4.5.2</span></span>|
|<span data-ttu-id="49da2-112">Type</span><span class="sxs-lookup"><span data-stu-id="49da2-112">Type</span></span>|<span data-ttu-id="49da2-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="49da2-113">Runtime</span></span>|
