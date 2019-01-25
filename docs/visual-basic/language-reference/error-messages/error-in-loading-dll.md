---
title: Chyba při načítání knihovny DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 76a0a443fd9f8a6dec5ead24bc75c97d89d6c36b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518459"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="78098-102">Chyba při načítání knihovny DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78098-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="78098-103">Dynamická knihovna (DLL) je knihovna podle `Lib` klauzuli `Declare` příkazu.</span><span class="sxs-lookup"><span data-stu-id="78098-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="78098-104">Možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="78098-104">Possible causes for this error include:</span></span>  
  
-   <span data-ttu-id="78098-105">Soubor není spustitelný soubor knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="78098-105">The file is not DLL executable.</span></span>  
  
-   <span data-ttu-id="78098-106">Soubor není knihovny DLL Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="78098-106">The file is not a Microsoft Windows DLL.</span></span>  
  
-   <span data-ttu-id="78098-107">Knihovnu DLL odkazuje na jiné knihovně DLL, která není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="78098-107">The DLL references another DLL that is not present.</span></span>  
  
-   <span data-ttu-id="78098-108">Knihovna DLL nebo odkazované knihovny DLL není v adresáři uvedeném na cestu.</span><span class="sxs-lookup"><span data-stu-id="78098-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="78098-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="78098-109">To correct this error</span></span>  
  
-   <span data-ttu-id="78098-110">Pokud je soubor zdroj textového souboru a proto není spustitelný soubor knihovny DLL, musí být zkompilovány a propojeny s DLL spustitelný soubor formuláře.</span><span class="sxs-lookup"><span data-stu-id="78098-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
-   <span data-ttu-id="78098-111">Pokud soubor není knihovny DLL Microsoft Windows, získáte odpovídající Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="78098-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
-   <span data-ttu-id="78098-112">Pokud je knihovna DLL odkazuje na jiné knihovně DLL, která není k dispozici, získejte odkazované knihovny DLL a ji dejte k dispozici.</span><span class="sxs-lookup"><span data-stu-id="78098-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
-   <span data-ttu-id="78098-113">Pokud knihovna DLL nebo odkazované knihovny DLL není v adresáři zadané cesty, přesune odkazovaný adresáře knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="78098-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78098-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78098-114">See also</span></span>
- [<span data-ttu-id="78098-115">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="78098-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
