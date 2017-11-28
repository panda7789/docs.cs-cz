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
ms.openlocfilehash: fc5a2e93541063a129efaa0ce08fc19a98372126
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="074b1-102">Byl zadán neplatný název protokolu událostí</span><span class="sxs-lookup"><span data-stu-id="074b1-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="074b1-103">Pro protokol událostí byl zadaný neplatný název.</span><span class="sxs-lookup"><span data-stu-id="074b1-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="074b1-104">To je obvykle způsobeno neplatných znaků v názvu, prázdný soubor název nebo název souboru, který je příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="074b1-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="074b1-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="074b1-105">To correct this error</span></span>  
  
-   <span data-ttu-id="074b1-106">Pokud zadaný název je více než osm znaků, ujistěte se, že nedojde ke konfliktu s názvy jiné protokoly událostí.</span><span class="sxs-lookup"><span data-stu-id="074b1-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="074b1-107">Při určování, pokud je název jedinečný vyhodnocují pouze prvních 8 znaků.</span><span class="sxs-lookup"><span data-stu-id="074b1-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
-   <span data-ttu-id="074b1-108">Pokud poskytuje cestu, ujistěte se, že je správně analyzovat.</span><span class="sxs-lookup"><span data-stu-id="074b1-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
-   <span data-ttu-id="074b1-109">Zkontrolujte, že neexistují žádné neplatné znaky v názvu.</span><span class="sxs-lookup"><span data-stu-id="074b1-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="074b1-110">Znaky, které nelze použít v názvu souboru obsahovat `<`, `>`, `:`, `"`, `/`, `\`, a `|`.</span><span class="sxs-lookup"><span data-stu-id="074b1-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="074b1-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="074b1-111">See Also</span></span>  
 [<span data-ttu-id="074b1-112">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="074b1-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [<span data-ttu-id="074b1-113">Postupy: přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="074b1-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [<span data-ttu-id="074b1-114">Postupy: vytváření a odebrání vlastní protokoly událostí</span><span class="sxs-lookup"><span data-stu-id="074b1-114">How to: Create and Remove Custom Event Logs</span></span>](http://msdn.microsoft.com/en-us/af9b7da0-80c7-46ac-b7f7-897063ddd503)
