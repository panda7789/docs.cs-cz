---
title: ImportTypes2 – metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f14822a58f3982d6f9fee1328c10b960657c056f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753501"
---
# <a name="importtypes2-method"></a><span data-ttu-id="ad522-102">ImportTypes2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ad522-102">ImportTypes2 Method</span></span>
<span data-ttu-id="ad522-103">Spustí import typů.</span><span class="sxs-lookup"><span data-stu-id="ad522-103">Initiates the import of types.</span></span> <span data-ttu-id="ad522-104">Volejte tuto metodu, abyste mohli naimportovat typy z každého oboru importují prostřednictvím [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="ad522-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad522-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad522-105">Syntax</span></span>  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad522-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad522-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ad522-107">ID sestavení, do kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="ad522-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ad522-108">ID souboru ze kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="ad522-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="ad522-109">Založený na nule oboru, ze kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="ad522-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="ad522-110">Získá popisovač výčtu pro typy v daném oboru.</span><span class="sxs-lookup"><span data-stu-id="ad522-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="ad522-111">Volitelně obdrží [imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ad522-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="ad522-112">Volitelně přijímá počet typů v zadaném oboru.</span><span class="sxs-lookup"><span data-stu-id="ad522-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad522-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ad522-113">Return Value</span></span>  
 <span data-ttu-id="ad522-114">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="ad522-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad522-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad522-115">Requirements</span></span>  
 <span data-ttu-id="ad522-116">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="ad522-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad522-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad522-117">See also</span></span>

- [<span data-ttu-id="ad522-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad522-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ad522-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad522-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ad522-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="ad522-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
