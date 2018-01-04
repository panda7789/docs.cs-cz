---
title: "Byl zadán neplatný název protokolu událostí"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76e4082710a6786ec5e743ce606e849637c26512
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="5caf8-102">Byl zadán neplatný název protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="5caf8-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="5caf8-103">Pro protokol událostí byl zadaný neplatný název.</span><span class="sxs-lookup"><span data-stu-id="5caf8-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="5caf8-104">To je obvykle způsobeno neplatných znaků v názvu, prázdný soubor název nebo název souboru, který je příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="5caf8-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5caf8-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5caf8-105">To correct this error</span></span>  
  
-   <span data-ttu-id="5caf8-106">Pokud zadaný název je více než osm znaků, ujistěte se, že nedojde ke konfliktu s názvy jiné protokoly událostí.</span><span class="sxs-lookup"><span data-stu-id="5caf8-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="5caf8-107">Při určování, pokud je název jedinečný vyhodnocují pouze prvních 8 znaků.</span><span class="sxs-lookup"><span data-stu-id="5caf8-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
-   <span data-ttu-id="5caf8-108">Pokud poskytuje cestu, ujistěte se, že je správně analyzovat.</span><span class="sxs-lookup"><span data-stu-id="5caf8-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
-   <span data-ttu-id="5caf8-109">Zkontrolujte, že neexistují žádné neplatné znaky v názvu.</span><span class="sxs-lookup"><span data-stu-id="5caf8-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="5caf8-110">Znaky, které nelze použít v názvu souboru obsahovat `<`, `>`, `:`, `"`, `/`, `\`, a `|`.</span><span class="sxs-lookup"><span data-stu-id="5caf8-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5caf8-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="5caf8-111">See Also</span></span>  
 [<span data-ttu-id="5caf8-112">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="5caf8-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [<span data-ttu-id="5caf8-113">Postupy: Přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="5caf8-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 
