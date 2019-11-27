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
ms.openlocfilehash: 9e91d990a8f23335248043c59eb210e8c4155e3a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445630"
---
# <a name="linkresource-method"></a><span data-ttu-id="37a54-102">LinkResource – metoda</span><span class="sxs-lookup"><span data-stu-id="37a54-102">LinkResource Method</span></span>
<span data-ttu-id="37a54-103">Odkazy v prostředku</span><span class="sxs-lookup"><span data-stu-id="37a54-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37a54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37a54-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="37a54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37a54-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="37a54-106">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="37a54-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="37a54-107">Název souboru</span><span class="sxs-lookup"><span data-stu-id="37a54-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="37a54-108">Volitelný nový název souboru.</span><span class="sxs-lookup"><span data-stu-id="37a54-108">Optional new file name.</span></span> <span data-ttu-id="37a54-109">Pokud není NULL, `pszFileName` bude zkopírována do pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="37a54-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="37a54-110">Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="37a54-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="37a54-111">Příznaky přístupnosti, například `mrPublic` a `mrPrivate`</span><span class="sxs-lookup"><span data-stu-id="37a54-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="37a54-112">Tento parametr může být předán [metodě DefineManifestResource –](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="37a54-112">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37a54-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="37a54-113">Return Value</span></span>  
 <span data-ttu-id="37a54-114">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="37a54-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37a54-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37a54-115">Requirements</span></span>  
 <span data-ttu-id="37a54-116">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="37a54-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37a54-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37a54-117">See also</span></span>

- [<span data-ttu-id="37a54-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a54-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="37a54-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37a54-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="37a54-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="37a54-120">ALink API</span></span>](index.md)
