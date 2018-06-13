---
title: Použití &#39;filegetobject –&#39; místo &#39;fileget –&#39; při použití argument typu &#39;objektu&#39;
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 2edb80f6df95774e0ea5a7b51e57925845d7ba75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640414"
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="c7318-102">Použití &#39;filegetobject –&#39; místo &#39;fileget –&#39; při použití argument typu &#39;objektu&#39;</span><span class="sxs-lookup"><span data-stu-id="c7318-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="c7318-103">`FileGet` Metoda obsahuje argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="c7318-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="c7318-104">`FileGetObject` musí být použito místo `FileGet` aby se zabránilo nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="c7318-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="c7318-105">Všimněte si, že funkce nabízené sítěmi `My.Computer.Filesystem` nabízí jednodušší používání a výkonu než buď `FileGet` nebo `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="c7318-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c7318-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c7318-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="c7318-107">Nahraďte `FileGet` s `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="c7318-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="c7318-108">Přetypování `Object` argument typu konkrétnější.</span><span class="sxs-lookup"><span data-stu-id="c7318-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7318-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7318-109">See Also</span></span>  
   
 [<span data-ttu-id="c7318-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="c7318-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
