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
ms.openlocfilehash: 61f82a34c287c62e1180c9c6bbe090914763afa3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479083"
---
# <a name="linkresource-method"></a><span data-ttu-id="4c837-102">LinkResource – metoda</span><span class="sxs-lookup"><span data-stu-id="4c837-102">LinkResource Method</span></span>
<span data-ttu-id="4c837-103">Odkazy v prostředku.</span><span class="sxs-lookup"><span data-stu-id="4c837-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c837-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c837-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c837-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c837-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4c837-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="4c837-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="4c837-107">Název souboru.</span><span class="sxs-lookup"><span data-stu-id="4c837-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="4c837-108">Volitelné nový název souboru.</span><span class="sxs-lookup"><span data-stu-id="4c837-108">Optional new file name.</span></span> <span data-ttu-id="4c837-109">Pokud není NULL, `pszFileName` bude zkopírován do pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="4c837-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="4c837-110">Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="4c837-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4c837-111">Usnadnění označí jako `mrPublic` a `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="4c837-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="4c837-112">Tento parametr může být předán [definemanifestresource – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="4c837-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c837-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4c837-113">Return Value</span></span>  
 <span data-ttu-id="4c837-114">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="4c837-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c837-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c837-115">Requirements</span></span>  
 <span data-ttu-id="4c837-116">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="4c837-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c837-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c837-117">See also</span></span>
- [<span data-ttu-id="4c837-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c837-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="4c837-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c837-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="4c837-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="4c837-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
