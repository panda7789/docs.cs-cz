---
title: Používat "Filegetobject –" místo 'FileGet', při použití argument typu 'Object'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: ddbe187ed1210d238448a5ff3feaee18beea1def
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2018
ms.locfileid: "53768008"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="13455-102">Používat "Filegetobject –" místo 'FileGet', při použití argument typu 'Object'</span><span class="sxs-lookup"><span data-stu-id="13455-102">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>
<span data-ttu-id="13455-103">`FileGet` Metoda zahrnuje argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="13455-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="13455-104">`FileGetObject` by měla sloužit místo `FileGet` chcete vyhnout se nejasnostem.</span><span class="sxs-lookup"><span data-stu-id="13455-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="13455-105">Všimněte si, že nabízí funkce `My.Computer.Filesystem` nabízí jednodušší využití a výkon než buď `FileGet` nebo `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="13455-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="13455-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="13455-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="13455-107">Nahraďte `FileGet` za `FileGetObject` (Jak velká může být moje znalostní báze?).</span><span class="sxs-lookup"><span data-stu-id="13455-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="13455-108">Přetypování `Object` konkrétnější typ argumentu.</span><span class="sxs-lookup"><span data-stu-id="13455-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13455-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="13455-109">See Also</span></span>  
   
 [<span data-ttu-id="13455-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="13455-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
