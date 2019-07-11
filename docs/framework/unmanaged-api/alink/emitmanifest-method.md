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
ms.openlocfilehash: 91dc4cb7d64d49d1e95c0c8eb79a29736559d842
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742081"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="fa2cb-102">EmitManifest – metoda</span><span class="sxs-lookup"><span data-stu-id="fa2cb-102">EmitManifest Method</span></span>
<span data-ttu-id="fa2cb-103">Generuje manifest finální.</span><span class="sxs-lookup"><span data-stu-id="fa2cb-103">Emits the final manifest.</span></span> <span data-ttu-id="fa2cb-104">Tuto metodu volejte po importu všechny ostatní soubory a nastavení všech možností.</span><span class="sxs-lookup"><span data-stu-id="fa2cb-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="fa2cb-105">Nevolejte tuto metodu pro nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="fa2cb-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa2cb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa2cb-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa2cb-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa2cb-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="fa2cb-108">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa2cb-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="fa2cb-109">Získá velikost pro rezervaci v souboru sestavení načtena z [strongnamesignaturesize – funkce](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="fa2cb-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="fa2cb-110">Volitelně přijme token manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa2cb-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa2cb-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fa2cb-111">Return Value</span></span>  
 <span data-ttu-id="fa2cb-112">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="fa2cb-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa2cb-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa2cb-113">Requirements</span></span>  
 <span data-ttu-id="fa2cb-114">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="fa2cb-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa2cb-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa2cb-115">See also</span></span>

- [<span data-ttu-id="fa2cb-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fa2cb-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="fa2cb-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fa2cb-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="fa2cb-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="fa2cb-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
