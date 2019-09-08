---
title: LinkResource – metoda
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 763b7a776007c2ce8dac42c6a5f7f00f6eb58a10
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776953"
---
# <a name="linkresource-method"></a><span data-ttu-id="9fa02-102">LinkResource – metoda</span><span class="sxs-lookup"><span data-stu-id="9fa02-102">LinkResource Method</span></span>
<span data-ttu-id="9fa02-103">Odkazy v prostředku</span><span class="sxs-lookup"><span data-stu-id="9fa02-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fa02-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fa02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fa02-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9fa02-106">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="9fa02-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="9fa02-107">Název souboru</span><span class="sxs-lookup"><span data-stu-id="9fa02-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="9fa02-108">Volitelný nový název souboru.</span><span class="sxs-lookup"><span data-stu-id="9fa02-108">Optional new file name.</span></span> <span data-ttu-id="9fa02-109">Pokud hodnota není null, `pszFileName` bude zkopírována do pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="9fa02-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="9fa02-110">Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="9fa02-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9fa02-111">Příznaky přístupnosti `mrPublic` , `mrPrivate`jako jsou a.</span><span class="sxs-lookup"><span data-stu-id="9fa02-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="9fa02-112">Tento parametr může být předán [metodě DefineManifestResource –](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="9fa02-112">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fa02-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9fa02-113">Return Value</span></span>  
 <span data-ttu-id="9fa02-114">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9fa02-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fa02-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fa02-115">Requirements</span></span>  
 <span data-ttu-id="9fa02-116">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="9fa02-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa02-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fa02-117">See also</span></span>

- [<span data-ttu-id="9fa02-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fa02-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9fa02-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fa02-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9fa02-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="9fa02-120">ALink API</span></span>](index.md)
