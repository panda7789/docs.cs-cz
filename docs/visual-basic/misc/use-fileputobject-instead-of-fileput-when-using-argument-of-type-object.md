---
title: Při použití argument typu 'Object' použít "FilePutObject" místo "FilePut.
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: 3d793151905c61ee12eccdfdb5e9567a4924bb35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022516"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a><span data-ttu-id="d4bfc-102">Při použití argument typu 'Object' použít "FilePutObject" místo "FilePut.</span><span class="sxs-lookup"><span data-stu-id="d4bfc-102">Use 'FilePutObject' instead of 'FilePut' when using argument of type 'Object'</span></span>
<span data-ttu-id="d4bfc-103">`FilePut` Metoda zahrnuje argument typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="d4bfc-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="d4bfc-104">`FilePutObject` by měla sloužit místo `FilePut` chcete vyhnout se nejasnostem.</span><span class="sxs-lookup"><span data-stu-id="d4bfc-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d4bfc-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d4bfc-105">To correct this error</span></span>  
  
- <span data-ttu-id="d4bfc-106">Nahraďte `FilePut` za `FilePutObject` (Jak velká může být moje znalostní báze?).</span><span class="sxs-lookup"><span data-stu-id="d4bfc-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
- <span data-ttu-id="d4bfc-107">Přetypování `Object` konkrétnější typ argumentu.</span><span class="sxs-lookup"><span data-stu-id="d4bfc-107">Cast the `Object` argument to a more specific type.</span></span>  
  
- <span data-ttu-id="d4bfc-108">Použití funkce, která je dostupná v `My.Computer.FileSystem` objektu.</span><span class="sxs-lookup"><span data-stu-id="d4bfc-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4bfc-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4bfc-109">See also</span></span>

- [<span data-ttu-id="d4bfc-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="d4bfc-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [<span data-ttu-id="d4bfc-111">My.Computer.FileSystem.WriteAllBytes</span><span class="sxs-lookup"><span data-stu-id="d4bfc-111">My.Computer.FileSystem.WriteAllBytes</span></span>](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
