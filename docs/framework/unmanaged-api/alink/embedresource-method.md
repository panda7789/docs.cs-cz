---
title: EmbedResource – metoda
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af5a200578c34464b5f8d86e568d08d814b46a29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742156"
---
# <a name="embedresource-method"></a><span data-ttu-id="841a2-102">EmbedResource – metoda</span><span class="sxs-lookup"><span data-stu-id="841a2-102">EmbedResource Method</span></span>
<span data-ttu-id="841a2-103">Deklaruje vložený prostředek.</span><span class="sxs-lookup"><span data-stu-id="841a2-103">Declares an embedded resource.</span></span> <span data-ttu-id="841a2-104">Tato metoda není ve skutečnosti vložit prostředek.</span><span class="sxs-lookup"><span data-stu-id="841a2-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="841a2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="841a2-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="841a2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="841a2-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="841a2-107">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="841a2-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="841a2-108">Soubor tokenu nebo sestavení ID souboru, který obsahuje prostředek.</span><span class="sxs-lookup"><span data-stu-id="841a2-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="841a2-109">Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="841a2-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="841a2-110">Posun prostředku z adresu RVA.</span><span class="sxs-lookup"><span data-stu-id="841a2-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="841a2-111">Usnadnění označí jako `mrPublic` a `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="841a2-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="841a2-112">Mohou být předány tyto příznaky [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="841a2-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="841a2-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="841a2-113">Return Value</span></span>  
 <span data-ttu-id="841a2-114">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="841a2-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="841a2-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="841a2-115">Requirements</span></span>  
 <span data-ttu-id="841a2-116">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="841a2-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="841a2-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="841a2-117">See also</span></span>

- [<span data-ttu-id="841a2-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="841a2-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="841a2-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="841a2-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="841a2-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="841a2-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
