---
title: EmitAssemblyCustomAttribute – metoda
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
ms.openlocfilehash: ec0a86e3396ad42152bc0a244f74ad13deba16e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446516"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="82f2c-102">EmitAssemblyCustomAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="82f2c-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="82f2c-103">Call to set assembly-level custom attributes.</span><span class="sxs-lookup"><span data-stu-id="82f2c-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f2c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82f2c-104">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="82f2c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82f2c-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="82f2c-106">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="82f2c-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="82f2c-107">File that defiles the attribute.</span><span class="sxs-lookup"><span data-stu-id="82f2c-107">File that defiles the attribute.</span></span> <span data-ttu-id="82f2c-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span><span class="sxs-lookup"><span data-stu-id="82f2c-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="82f2c-109">Type of the custom attribute.</span><span class="sxs-lookup"><span data-stu-id="82f2c-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="82f2c-110">Custom value data.</span><span class="sxs-lookup"><span data-stu-id="82f2c-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="82f2c-111">Length of custom value data.</span><span class="sxs-lookup"><span data-stu-id="82f2c-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="82f2c-112">TRUE if the custom attribute is related to assembly signing.</span><span class="sxs-lookup"><span data-stu-id="82f2c-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="82f2c-113">TRUE if multiple attributes are to be emitted.</span><span class="sxs-lookup"><span data-stu-id="82f2c-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82f2c-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="82f2c-114">Return Value</span></span>  
 <span data-ttu-id="82f2c-115">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="82f2c-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82f2c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82f2c-116">Requirements</span></span>  
 <span data-ttu-id="82f2c-117">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="82f2c-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f2c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82f2c-118">See also</span></span>

- [<span data-ttu-id="82f2c-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82f2c-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="82f2c-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82f2c-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="82f2c-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="82f2c-121">ALink API</span></span>](index.md)
