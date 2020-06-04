---
title: Pro protokol událostí byl zadán neplatný název.
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 70b1de2a3776a9c68260cc431b65e754d7247a0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412920"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="e51c0-102">Pro protokol událostí byl zadán neplatný název.</span><span class="sxs-lookup"><span data-stu-id="e51c0-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="e51c0-103">Pro protokol událostí byl zadán neplatný název.</span><span class="sxs-lookup"><span data-stu-id="e51c0-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="e51c0-104">Obvykle se jedná o výsledek neplatných znaků v názvu, prázdný název souboru nebo název souboru, který je příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="e51c0-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e51c0-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e51c0-105">To correct this error</span></span>  
  
- <span data-ttu-id="e51c0-106">Pokud je zadaný název delší než osm znaků, ujistěte se, že nedochází ke konfliktu s názvy jiných protokolů událostí.</span><span class="sxs-lookup"><span data-stu-id="e51c0-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="e51c0-107">Při určování, jestli je název jedinečný, se vyhodnotí jenom prvních osm znaků.</span><span class="sxs-lookup"><span data-stu-id="e51c0-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="e51c0-108">Pokud zadáváte cestu, ujistěte se, že je správně analyzovaná.</span><span class="sxs-lookup"><span data-stu-id="e51c0-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="e51c0-109">Ověřte, zda název neobsahuje neplatné znaky.</span><span class="sxs-lookup"><span data-stu-id="e51c0-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="e51c0-110">Mezi znaky, které nelze použít v názvu souboru `<` , patří, `>` , `:` , `"` ,, a `/` `\` `|` .</span><span class="sxs-lookup"><span data-stu-id="e51c0-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e51c0-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="e51c0-111">See also</span></span>

- [<span data-ttu-id="e51c0-112">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="e51c0-112">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="e51c0-113">Postupy: Přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="e51c0-113">How to: Rename a File</span></span>](../developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
