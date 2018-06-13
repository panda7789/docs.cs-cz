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
ms.openlocfilehash: 5ed9645c5111e7260010df74554825ffd8d427e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402142"
---
# <a name="getscope2-method"></a><span data-ttu-id="c92e0-102">GetScope2 – metoda</span><span class="sxs-lookup"><span data-stu-id="c92e0-102">GetScope2 Method</span></span>
<span data-ttu-id="c92e0-103">Získá obor importu.</span><span class="sxs-lookup"><span data-stu-id="c92e0-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c92e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c92e0-104">Syntax</span></span>  
  
```  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="c92e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c92e0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c92e0-106">ID cílového sestavení.</span><span class="sxs-lookup"><span data-stu-id="c92e0-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c92e0-107">ID souboru, ze kterých chcete importovat.</span><span class="sxs-lookup"><span data-stu-id="c92e0-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="c92e0-108">Počítaný od nuly oboru pro import.</span><span class="sxs-lookup"><span data-stu-id="c92e0-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="c92e0-109">Obdrží ukazatel na [imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) rozhraní pro zadaný obor.</span><span class="sxs-lookup"><span data-stu-id="c92e0-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c92e0-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c92e0-110">Return Value</span></span>  
 <span data-ttu-id="c92e0-111">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="c92e0-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c92e0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c92e0-112">Requirements</span></span>  
 <span data-ttu-id="c92e0-113">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="c92e0-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c92e0-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c92e0-114">See Also</span></span>  
 [<span data-ttu-id="c92e0-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c92e0-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c92e0-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c92e0-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c92e0-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="c92e0-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
