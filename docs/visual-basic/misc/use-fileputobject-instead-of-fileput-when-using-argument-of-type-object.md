---
title: "Použít & č. 39; FilePutObject – & č. 39; místo & č. 39; FilePut – & č. 39; Při použití argument typu & č. 39; objekt & č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cba4af206e2dbf767fdb883ec81229a67842c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="fb866-102">Použít & č. 39; FilePutObject – & č. 39; místo & č. 39; FilePut – & č. 39; Při použití argument typu & č. 39; objekt & č. 39;</span><span class="sxs-lookup"><span data-stu-id="fb866-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="fb866-103">`FilePut` Metoda obsahuje argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="fb866-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="fb866-104">`FilePutObject`musí být použito místo `FilePut` aby se zabránilo nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="fb866-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fb866-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fb866-105">To correct this error</span></span>  
  
-   <span data-ttu-id="fb866-106">Nahraďte `FilePut` s `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="fb866-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="fb866-107">Přetypování `Object` argument typu konkrétnější.</span><span class="sxs-lookup"><span data-stu-id="fb866-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="fb866-108">Používat funkce, které jsou k dispozici v `My.Computer.FileSystem` objektu.</span><span class="sxs-lookup"><span data-stu-id="fb866-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb866-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb866-109">See Also</span></span>  
 [<span data-ttu-id="fb866-110">NENÍ v sestavení: FilePutObject – funkce</span><span class="sxs-lookup"><span data-stu-id="fb866-110">NOT IN BUILD: FilePutObject Function</span></span>](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b)  
 [<span data-ttu-id="fb866-111">My.Computer.FileSystem – objekt</span><span class="sxs-lookup"><span data-stu-id="fb866-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)  
 [<span data-ttu-id="fb866-112">My.Computer.FileSystem.WriteAllBytes – metoda</span><span class="sxs-lookup"><span data-stu-id="fb866-112">My.Computer.FileSystem.WriteAllBytes Method</span></span>](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)
