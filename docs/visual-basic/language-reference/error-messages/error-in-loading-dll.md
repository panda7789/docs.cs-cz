---
title: Chyba při načítání knihovny DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: c3f88a5a3c37c89d23055aa413957b2add38ed67
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816899"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="011dd-102">Chyba při načítání knihovny DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="011dd-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="011dd-103">Dynamická knihovna (DLL) je knihovna podle `Lib` klauzuli `Declare` příkazu.</span><span class="sxs-lookup"><span data-stu-id="011dd-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="011dd-104">Možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="011dd-104">Possible causes for this error include:</span></span>  
  
-   <span data-ttu-id="011dd-105">Soubor není spustitelný soubor knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="011dd-105">The file is not DLL executable.</span></span>  
  
-   <span data-ttu-id="011dd-106">Soubor není knihovny DLL Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="011dd-106">The file is not a Microsoft Windows DLL.</span></span>  
  
-   <span data-ttu-id="011dd-107">Knihovnu DLL odkazuje na jiné knihovně DLL, která není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="011dd-107">The DLL references another DLL that is not present.</span></span>  
  
-   <span data-ttu-id="011dd-108">Knihovna DLL nebo odkazované knihovny DLL není v adresáři uvedeném na cestu.</span><span class="sxs-lookup"><span data-stu-id="011dd-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="011dd-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="011dd-109">To correct this error</span></span>  
  
-   <span data-ttu-id="011dd-110">Pokud je soubor zdroj textového souboru a proto není spustitelný soubor knihovny DLL, musí být zkompilovány a propojeny s DLL spustitelný soubor formuláře.</span><span class="sxs-lookup"><span data-stu-id="011dd-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
-   <span data-ttu-id="011dd-111">Pokud soubor není knihovny DLL Microsoft Windows, získáte odpovídající Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="011dd-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
-   <span data-ttu-id="011dd-112">Pokud je knihovna DLL odkazuje na jiné knihovně DLL, která není k dispozici, získejte odkazované knihovny DLL a ji dejte k dispozici.</span><span class="sxs-lookup"><span data-stu-id="011dd-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
-   <span data-ttu-id="011dd-113">Pokud knihovna DLL nebo odkazované knihovny DLL není v adresáři zadané cesty, přesune odkazovaný adresáře knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="011dd-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="011dd-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="011dd-114">See also</span></span>

- [<span data-ttu-id="011dd-115">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="011dd-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
