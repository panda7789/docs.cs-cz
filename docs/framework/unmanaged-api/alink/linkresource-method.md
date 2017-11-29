---
title: "LinkResource – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.LinkResource
api_location: alink.dll
api_type: COM
f1_keywords: LinkResource
helpviewer_keywords: LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8cb1f985c1d735fa20507ab90d478e97025c9e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-method"></a><span data-ttu-id="bb844-102">LinkResource – metoda</span><span class="sxs-lookup"><span data-stu-id="bb844-102">LinkResource Method</span></span>
<span data-ttu-id="bb844-103">Odkazy v prostředku.</span><span class="sxs-lookup"><span data-stu-id="bb844-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb844-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb844-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb844-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb844-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="bb844-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="bb844-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="bb844-107">Název souboru.</span><span class="sxs-lookup"><span data-stu-id="bb844-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="bb844-108">Volitelné nový název souboru.</span><span class="sxs-lookup"><span data-stu-id="bb844-108">Optional new file name.</span></span> <span data-ttu-id="bb844-109">Pokud není hodnotou NULL, `pszFileName` bude zkopírován do pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="bb844-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="bb844-110">Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="bb844-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="bb844-111">Usnadnění flags – například `mrPublic` a `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="bb844-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="bb844-112">Tento parametr může být předán [DefineManifestResource – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="bb844-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb844-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bb844-113">Return Value</span></span>  
 <span data-ttu-id="bb844-114">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="bb844-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb844-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb844-115">Requirements</span></span>  
 <span data-ttu-id="bb844-116">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="bb844-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb844-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb844-117">See Also</span></span>  
 [<span data-ttu-id="bb844-118">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb844-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="bb844-119">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb844-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="bb844-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="bb844-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
