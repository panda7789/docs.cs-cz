---
title: Používat "Filegetobject –" místo 'FileGet', při použití argument typu 'Object'
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 60eaabc686070aced908116728f06d4e82b5cecb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723391"
---
# <a name="use-filegetobject-instead-of-fileget-when-using-argument-of-type-object"></a><span data-ttu-id="93910-102">Používat "Filegetobject –" místo 'FileGet', při použití argument typu 'Object'</span><span class="sxs-lookup"><span data-stu-id="93910-102">Use 'FileGetObject' instead of 'FileGet' when using argument of type 'Object'</span></span>
<span data-ttu-id="93910-103">`FileGet` Metoda zahrnuje argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="93910-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="93910-104">`FileGetObject` by měla sloužit místo `FileGet` chcete vyhnout se nejasnostem.</span><span class="sxs-lookup"><span data-stu-id="93910-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="93910-105">Všimněte si, že nabízí funkce `My.Computer.Filesystem` nabízí jednodušší využití a výkon než buď `FileGet` nebo `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="93910-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="93910-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="93910-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="93910-107">Nahraďte `FileGet` za `FileGetObject` (Jak velká může být moje znalostní báze?).</span><span class="sxs-lookup"><span data-stu-id="93910-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="93910-108">Přetypování `Object` konkrétnější typ argumentu.</span><span class="sxs-lookup"><span data-stu-id="93910-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93910-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93910-109">See also</span></span>

- [<span data-ttu-id="93910-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="93910-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
