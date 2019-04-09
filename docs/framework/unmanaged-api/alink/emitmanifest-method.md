---
title: EmitManifest – metoda
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 051b5f47db05301f3a3326a2cc4cc5cf5c8b1ec2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137823"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="8670f-102">EmitManifest – metoda</span><span class="sxs-lookup"><span data-stu-id="8670f-102">EmitManifest Method</span></span>
<span data-ttu-id="8670f-103">Generuje manifest finální.</span><span class="sxs-lookup"><span data-stu-id="8670f-103">Emits the final manifest.</span></span> <span data-ttu-id="8670f-104">Tuto metodu volejte po importu všechny ostatní soubory a nastavení všech možností.</span><span class="sxs-lookup"><span data-stu-id="8670f-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="8670f-105">Nevolejte tuto metodu pro nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="8670f-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8670f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8670f-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8670f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="8670f-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8670f-108">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="8670f-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="8670f-109">Získá velikost pro rezervaci v souboru sestavení načtena z [strongnamesignaturesize – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="8670f-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="8670f-110">Volitelně přijme token manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="8670f-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8670f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8670f-111">Return Value</span></span>  
 <span data-ttu-id="8670f-112">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="8670f-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8670f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8670f-113">Requirements</span></span>  
 <span data-ttu-id="8670f-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="8670f-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8670f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8670f-115">See also</span></span>

- [<span data-ttu-id="8670f-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8670f-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="8670f-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8670f-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="8670f-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="8670f-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
