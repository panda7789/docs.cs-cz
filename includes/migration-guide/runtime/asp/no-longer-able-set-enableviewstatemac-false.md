---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803242"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="846e9-101">Již nelze nastavit EnableViewStateMac na false</span><span class="sxs-lookup"><span data-stu-id="846e9-101">No longer able to set EnableViewStateMac to false</span></span>

|   |   |
|---|---|
|<span data-ttu-id="846e9-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="846e9-102">Details</span></span>|<span data-ttu-id="846e9-103">ASP.NET již umožňuje vývojářům specifikovat <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> nebo <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="846e9-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="846e9-104">Ověřovací kód zprávy stavu zobrazení (MAC) je nyní vynucen pro všechny požadavky s vloženým stavem zobrazení.</span><span class="sxs-lookup"><span data-stu-id="846e9-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="846e9-105">Ovlivněny <code>false</code> jsou pouze aplikace, které explicitně nastavují vlastnost EnableViewStateMac.</span><span class="sxs-lookup"><span data-stu-id="846e9-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>|
|<span data-ttu-id="846e9-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="846e9-106">Suggestion</span></span>|<span data-ttu-id="846e9-107">EnableViewStateMac musí být považován za true a všechny výsledné chyby MAC musí být vyřešeny (jak je vysvětleno v [tomto návodu](https://support.microsoft.com/kb/2915218), který obsahuje více rozlišení v závislosti na specifika toho, co je příčinou chyb MAC).</span><span class="sxs-lookup"><span data-stu-id="846e9-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>|
|<span data-ttu-id="846e9-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="846e9-108">Scope</span></span>|<span data-ttu-id="846e9-109">Hlavní</span><span class="sxs-lookup"><span data-stu-id="846e9-109">Major</span></span>|
|<span data-ttu-id="846e9-110">Version</span><span class="sxs-lookup"><span data-stu-id="846e9-110">Version</span></span>|<span data-ttu-id="846e9-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="846e9-111">4.5.2</span></span>|
|<span data-ttu-id="846e9-112">Typ</span><span class="sxs-lookup"><span data-stu-id="846e9-112">Type</span></span>|<span data-ttu-id="846e9-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="846e9-113">Runtime</span></span>|
