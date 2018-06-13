---
title: Chyba při načítání knihovny DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: ac21c4d52b248025ee26bac3e511bb5b0a0b668e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584680"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="4fdac-102">Chyba při načítání knihovny DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fdac-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="4fdac-103">Dynamická knihovna (DLL) je zadána v knihovna `Lib` klauzuli `Declare` příkaz.</span><span class="sxs-lookup"><span data-stu-id="4fdac-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="4fdac-104">Možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="4fdac-104">Possible causes for this error include:</span></span>  
  
-   <span data-ttu-id="4fdac-105">Soubor není spustitelný soubor knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="4fdac-105">The file is not DLL executable.</span></span>  
  
-   <span data-ttu-id="4fdac-106">Soubor není knihovny DLL Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="4fdac-106">The file is not a Microsoft Windows DLL.</span></span>  
  
-   <span data-ttu-id="4fdac-107">Knihovny DLL odkazuje na jiné knihovny DLL, která není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4fdac-107">The DLL references another DLL that is not present.</span></span>  
  
-   <span data-ttu-id="4fdac-108">Knihovny DLL nebo odkazované DLL není v adresáři zadaném v cestě.</span><span class="sxs-lookup"><span data-stu-id="4fdac-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4fdac-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4fdac-109">To correct this error</span></span>  
  
-   <span data-ttu-id="4fdac-110">Pokud je soubor zdroj textového souboru a proto není spustitelný soubor knihovny DLL, musí být zkompilovány a propojené s formuláři DLL-spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="4fdac-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
-   <span data-ttu-id="4fdac-111">Pokud není soubor knihovny DLL Microsoft Windows, získejte ekvivalentní Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="4fdac-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
-   <span data-ttu-id="4fdac-112">Pokud knihovnu DLL odkazuje na jiné knihovny DLL, která není k dispozici, získat odkazované DLL a zpřístupnit jej.</span><span class="sxs-lookup"><span data-stu-id="4fdac-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
-   <span data-ttu-id="4fdac-113">Pokud knihovnu DLL nebo odkazované DLL není v zadané cestě adresáře, přesuňte knihovnu DLL odkazované adresáře.</span><span class="sxs-lookup"><span data-stu-id="4fdac-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fdac-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fdac-114">See Also</span></span>  
 [<span data-ttu-id="4fdac-115">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="4fdac-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
