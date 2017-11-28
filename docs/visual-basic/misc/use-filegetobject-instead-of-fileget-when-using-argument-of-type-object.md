---
title: "Použít & č. 39; Filegetobject – & č. 39; místo & č. 39; Fileget – & č. 39; Při použití argument typu & č. 39; objekt & č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 996e8a50f90c738bbc64c200125a785c0e9bcd58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="7fd4d-102">Použít & č. 39; Filegetobject – & č. 39; místo & č. 39; Fileget – & č. 39; Při použití argument typu & č. 39; objekt & č. 39;</span><span class="sxs-lookup"><span data-stu-id="7fd4d-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="7fd4d-103">`FileGet` Metoda obsahuje argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="7fd4d-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="7fd4d-104">`FileGetObject`musí být použito místo `FileGet` aby se zabránilo nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="7fd4d-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="7fd4d-105">Všimněte si, že funkce nabízené sítěmi `My.Computer.Filesystem` nabízí jednodušší používání a výkonu než buď `FileGet` nebo `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="7fd4d-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7fd4d-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7fd4d-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="7fd4d-107">Nahraďte `FileGet` s `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="7fd4d-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="7fd4d-108">Přetypování `Object` argument typu konkrétnější.</span><span class="sxs-lookup"><span data-stu-id="7fd4d-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fd4d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="7fd4d-109">See Also</span></span>  
 [<span data-ttu-id="7fd4d-110">NENÍ v sestavení: Filegetobject – funkce</span><span class="sxs-lookup"><span data-stu-id="7fd4d-110">NOT IN BUILD: FileGetObject Function</span></span>](http://msdn.microsoft.com/en-us/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)  
 [<span data-ttu-id="7fd4d-111">My.Computer.FileSystem – objekt</span><span class="sxs-lookup"><span data-stu-id="7fd4d-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)
