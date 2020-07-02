---
ms.openlocfilehash: f980c8029375074889505a8eb7e8a65aaa8d74e4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614517"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a><span data-ttu-id="94549-101">Resgen odmítá načíst obsah z webu.</span><span class="sxs-lookup"><span data-stu-id="94549-101">Resgen refuses to load content from the web</span></span>

#### <a name="details"></a><span data-ttu-id="94549-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="94549-102">Details</span></span>

<span data-ttu-id="94549-103">soubory RESX mohou obsahovat binární formátovaný vstup.</span><span class="sxs-lookup"><span data-stu-id="94549-103">.resx files may contain binary formatted input.</span></span> <span data-ttu-id="94549-104">Pokud se pokusíte použít Resgen k načtení souboru staženého z nedůvěryhodného umístění, ve výchozím nastavení se nepodaří načíst vstup.</span><span class="sxs-lookup"><span data-stu-id="94549-104">If you attempt to use resgen to load a file that was downloaded from an untrusted location, it will fail to load the input by default.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="94549-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="94549-105">Suggestion</span></span>

<span data-ttu-id="94549-106">Uživatelé Resgen, kteří vyžadují načítání binárního formátovaného vstupu z nedůvěryhodných umístění, mohou buď odebrat značku webu ze vstupního souboru, nebo použít Quirk pro odhlášení. Přidejte následující nastavení registru, aby bylo možné použít Quirk pro místní počítač: [HKEY_LOCAL_MACHINE \software\microsoft.netframework\sdk] &quot; AllowProcessOfUntrustedResourceFiles &quot; = &quot; true&quot;</span><span class="sxs-lookup"><span data-stu-id="94549-106">Resgen users who require loading binary formatted input from untrusted locations can either remove the mark of the web from the input file or apply the opt-out quirk.Add the following registry setting to apply the machine wide opt-out quirk: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;</span></span>

| <span data-ttu-id="94549-107">Name</span><span class="sxs-lookup"><span data-stu-id="94549-107">Name</span></span>    | <span data-ttu-id="94549-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="94549-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="94549-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="94549-109">Scope</span></span>   | <span data-ttu-id="94549-110">Edge</span><span class="sxs-lookup"><span data-stu-id="94549-110">Edge</span></span>        |
| <span data-ttu-id="94549-111">Verze</span><span class="sxs-lookup"><span data-stu-id="94549-111">Version</span></span> | <span data-ttu-id="94549-112">4.7.2</span><span class="sxs-lookup"><span data-stu-id="94549-112">4.7.2</span></span>       |
| <span data-ttu-id="94549-113">Typ</span><span class="sxs-lookup"><span data-stu-id="94549-113">Type</span></span>    | <span data-ttu-id="94549-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="94549-114">Retargeting</span></span> |
