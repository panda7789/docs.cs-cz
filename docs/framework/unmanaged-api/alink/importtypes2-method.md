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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098465"
---
# <a name="importtypes2-method"></a><span data-ttu-id="4d34c-102">ImportTypes2 – metoda</span><span class="sxs-lookup"><span data-stu-id="4d34c-102">ImportTypes2 Method</span></span>
<span data-ttu-id="4d34c-103">Spustí import typů.</span><span class="sxs-lookup"><span data-stu-id="4d34c-103">Initiates the import of types.</span></span> <span data-ttu-id="4d34c-104">Volejte tuto metodu, abyste mohli naimportovat typy z každého oboru importují prostřednictvím [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="4d34c-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d34c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d34c-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4d34c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d34c-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4d34c-107">ID sestavení, do kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="4d34c-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4d34c-108">ID souboru ze kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="4d34c-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="4d34c-109">Založený na nule oboru, ze kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="4d34c-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="4d34c-110">Získá popisovač výčtu pro typy v daném oboru.</span><span class="sxs-lookup"><span data-stu-id="4d34c-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="4d34c-111">Volitelně obdrží [imetadataimport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d34c-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="4d34c-112">Volitelně přijímá počet typů v zadaném oboru.</span><span class="sxs-lookup"><span data-stu-id="4d34c-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d34c-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4d34c-113">Return Value</span></span>  
 <span data-ttu-id="4d34c-114">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="4d34c-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d34c-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d34c-115">Requirements</span></span>  
 <span data-ttu-id="4d34c-116">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="4d34c-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d34c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d34c-117">See also</span></span>

- [<span data-ttu-id="4d34c-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d34c-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="4d34c-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d34c-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="4d34c-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="4d34c-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
