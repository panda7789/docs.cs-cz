---
title: Chyba při načítání knihovny DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: fd2e425f2dd3f4127cd777d4a1f7ab9809de9d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409621"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="9da3e-102">Chyba při načítání knihovny DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9da3e-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="9da3e-103">Knihovna DLL (Dynamic-Link Library) je knihovna zadaná v `Lib` klauzuli `Declare` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9da3e-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="9da3e-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="9da3e-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="9da3e-105">Soubor není spustitelný soubor DLL.</span><span class="sxs-lookup"><span data-stu-id="9da3e-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="9da3e-106">Soubor není knihovna DLL systému Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="9da3e-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="9da3e-107">Knihovna DLL odkazuje na jinou knihovnu DLL, která není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9da3e-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="9da3e-108">Knihovna DLL nebo odkazovaná knihovna DLL nejsou v adresáři zadaném v cestě.</span><span class="sxs-lookup"><span data-stu-id="9da3e-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9da3e-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9da3e-109">To correct this error</span></span>  
  
- <span data-ttu-id="9da3e-110">Pokud se jedná o zdrojový textový soubor, a proto ne spustitelný soubor DLL, musí být zkompilován a propojen s formulářem spustitelného souboru DLL.</span><span class="sxs-lookup"><span data-stu-id="9da3e-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="9da3e-111">Pokud soubor není knihovna DLL systému Microsoft Windows, Získejte ekvivalent systému Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="9da3e-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="9da3e-112">Pokud knihovna DLL odkazuje na jinou knihovnu DLL, která není k dispozici, Získejte odkazovanou knihovnu DLL a zpřístupněte ji.</span><span class="sxs-lookup"><span data-stu-id="9da3e-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="9da3e-113">Pokud knihovna DLL nebo odkazovaná knihovna DLL není v adresáři určeném cestou, přesuňte knihovnu DLL do odkazovaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="9da3e-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da3e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9da3e-114">See also</span></span>

- [<span data-ttu-id="9da3e-115">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="9da3e-115">Declare Statement</span></span>](../statements/declare-statement.md)
