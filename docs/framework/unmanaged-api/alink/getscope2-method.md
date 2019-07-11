---
title: GetScope2 – metoda
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c0abc63610f3f1ed6e8a556c44ee15edc1ea20b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741838"
---
# <a name="getscope2-method"></a><span data-ttu-id="359f9-102">GetScope2 – metoda</span><span class="sxs-lookup"><span data-stu-id="359f9-102">GetScope2 Method</span></span>
<span data-ttu-id="359f9-103">Získá obor importu.</span><span class="sxs-lookup"><span data-stu-id="359f9-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="359f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="359f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="359f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="359f9-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="359f9-106">ID cílového sestavení.</span><span class="sxs-lookup"><span data-stu-id="359f9-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="359f9-107">ID souboru, ze kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="359f9-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="359f9-108">Založený na nule oboru k importu.</span><span class="sxs-lookup"><span data-stu-id="359f9-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="359f9-109">Přijímá ukazatel na [imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) rozhraní pro zadaný obor.</span><span class="sxs-lookup"><span data-stu-id="359f9-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="359f9-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="359f9-110">Return Value</span></span>  
 <span data-ttu-id="359f9-111">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="359f9-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="359f9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="359f9-112">Requirements</span></span>  
 <span data-ttu-id="359f9-113">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="359f9-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="359f9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="359f9-114">See also</span></span>

- [<span data-ttu-id="359f9-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="359f9-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="359f9-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="359f9-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="359f9-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="359f9-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
