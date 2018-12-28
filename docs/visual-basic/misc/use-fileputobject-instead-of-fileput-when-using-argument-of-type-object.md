---
title: Při použití argument typu 'Object' použít "FilePutObject" místo "FilePut.
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: df7d7c54992984bcb1684e41f60ae8361a3aed03
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2018
ms.locfileid: "53774222"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="53b4a-102">Při použití argument typu 'Object' použít "FilePutObject" místo "FilePut.</span><span class="sxs-lookup"><span data-stu-id="53b4a-102">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>
<span data-ttu-id="53b4a-103">`FilePut` Metoda zahrnuje argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="53b4a-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="53b4a-104">`FilePutObject` by měla sloužit místo `FilePut` chcete vyhnout se nejasnostem.</span><span class="sxs-lookup"><span data-stu-id="53b4a-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="53b4a-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="53b4a-105">To correct this error</span></span>  
  
-   <span data-ttu-id="53b4a-106">Nahraďte `FilePut` za `FilePutObject` (Jak velká může být moje znalostní báze?).</span><span class="sxs-lookup"><span data-stu-id="53b4a-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="53b4a-107">Přetypování `Object` konkrétnější typ argumentu.</span><span class="sxs-lookup"><span data-stu-id="53b4a-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="53b4a-108">Použití funkce, která je dostupná v `My.Computer.FileSystem` objektu.</span><span class="sxs-lookup"><span data-stu-id="53b4a-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b4a-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="53b4a-109">See Also</span></span>  
   
 [<span data-ttu-id="53b4a-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="53b4a-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)  
 [<span data-ttu-id="53b4a-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="53b4a-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
