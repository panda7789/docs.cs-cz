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
ms.openlocfilehash: cc986dc27deb08f779a9654324e6832d8420554a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587131"
---
# <a name="getscope2-method"></a><span data-ttu-id="bcee2-102">GetScope2 – metoda</span><span class="sxs-lookup"><span data-stu-id="bcee2-102">GetScope2 Method</span></span>
<span data-ttu-id="bcee2-103">Získá obor importu.</span><span class="sxs-lookup"><span data-stu-id="bcee2-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcee2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcee2-104">Syntax</span></span>  
  
```  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="bcee2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcee2-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="bcee2-106">ID cílového sestavení.</span><span class="sxs-lookup"><span data-stu-id="bcee2-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="bcee2-107">ID souboru, ze kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="bcee2-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="bcee2-108">Založený na nule oboru k importu.</span><span class="sxs-lookup"><span data-stu-id="bcee2-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="bcee2-109">Přijímá ukazatel na [imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) rozhraní pro zadaný obor.</span><span class="sxs-lookup"><span data-stu-id="bcee2-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bcee2-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bcee2-110">Return Value</span></span>  
 <span data-ttu-id="bcee2-111">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="bcee2-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcee2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bcee2-112">Requirements</span></span>  
 <span data-ttu-id="bcee2-113">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="bcee2-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcee2-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcee2-114">See also</span></span>
- [<span data-ttu-id="bcee2-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcee2-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="bcee2-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcee2-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="bcee2-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="bcee2-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
