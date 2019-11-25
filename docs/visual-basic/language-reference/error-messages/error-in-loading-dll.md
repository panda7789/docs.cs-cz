---
title: Chyba při načítání knihovny DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 36452cc6ff03042939cd4066aef76129b5bb8f0a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329556"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="bd77d-102">Chyba při načítání knihovny DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd77d-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="bd77d-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span><span class="sxs-lookup"><span data-stu-id="bd77d-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="bd77d-104">Possible causes for this error include:</span><span class="sxs-lookup"><span data-stu-id="bd77d-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="bd77d-105">The file is not DLL executable.</span><span class="sxs-lookup"><span data-stu-id="bd77d-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="bd77d-106">The file is not a Microsoft Windows DLL.</span><span class="sxs-lookup"><span data-stu-id="bd77d-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="bd77d-107">The DLL references another DLL that is not present.</span><span class="sxs-lookup"><span data-stu-id="bd77d-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="bd77d-108">The DLL or referenced DLL is not in a directory specified in the path.</span><span class="sxs-lookup"><span data-stu-id="bd77d-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd77d-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="bd77d-109">To correct this error</span></span>  
  
- <span data-ttu-id="bd77d-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span><span class="sxs-lookup"><span data-stu-id="bd77d-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="bd77d-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span><span class="sxs-lookup"><span data-stu-id="bd77d-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="bd77d-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span><span class="sxs-lookup"><span data-stu-id="bd77d-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="bd77d-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span><span class="sxs-lookup"><span data-stu-id="bd77d-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd77d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd77d-114">See also</span></span>

- [<span data-ttu-id="bd77d-115">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="bd77d-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
