---
title: Byl zadán neplatný název protokolu událostí
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 2b9c934272d0f3392c845dcd2f0062a98dc50c7b
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58032265"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="1a75c-102">Byl zadán neplatný název protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="1a75c-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="1a75c-103">Pro protokol událostí byl zadán neplatný název.</span><span class="sxs-lookup"><span data-stu-id="1a75c-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="1a75c-104">Obvykle to je výsledkem neplatných znaků v názvu, prázdný soubor název nebo název souboru, který je příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="1a75c-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1a75c-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1a75c-105">To correct this error</span></span>  
  
-   <span data-ttu-id="1a75c-106">Pokud se zadaným názvem více než osm znaků, ujistěte se, že nedojde ke konfliktu s názvy jiných protokolů událostí.</span><span class="sxs-lookup"><span data-stu-id="1a75c-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="1a75c-107">Pouze prvních osm znaků se vyhodnocují při určování, jestli je název jedinečný.</span><span class="sxs-lookup"><span data-stu-id="1a75c-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
-   <span data-ttu-id="1a75c-108">Pokud se zadáním cesty, ujistěte se, že je správně parsovat.</span><span class="sxs-lookup"><span data-stu-id="1a75c-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
-   <span data-ttu-id="1a75c-109">Zkontrolujte, že neexistují žádné neplatné znaky v názvu.</span><span class="sxs-lookup"><span data-stu-id="1a75c-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="1a75c-110">Znaky, které nelze použít v názvu souboru patří `<`, `>`, `:`, `"`, `/`, `\`, a `|`.</span><span class="sxs-lookup"><span data-stu-id="1a75c-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a75c-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a75c-111">See also</span></span>

- [<span data-ttu-id="1a75c-112">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="1a75c-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="1a75c-113">Postupy: Přejmenovat soubor</span><span class="sxs-lookup"><span data-stu-id="1a75c-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
