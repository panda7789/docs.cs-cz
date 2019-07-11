---
title: ImportFileEx – metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fcf714cb0c1c1dd59ae2ec56279870c0bb3e1c4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741719"
---
# <a name="importfileex-method"></a><span data-ttu-id="cd2b9-102">ImportFileEx – metoda</span><span class="sxs-lookup"><span data-stu-id="cd2b9-102">ImportFileEx Method</span></span>
<span data-ttu-id="cd2b9-103">Importy určili sestavení nebo nevázaného modulu.</span><span class="sxs-lookup"><span data-stu-id="cd2b9-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd2b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd2b9-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd2b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd2b9-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="cd2b9-106">Plně kvalifikovaný název souboru, ze kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="cd2b9-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="cd2b9-107">Volitelný název cílového souboru.</span><span class="sxs-lookup"><span data-stu-id="cd2b9-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="cd2b9-108">Při hodnotě TRUE se používá importtypes –, jinak se import je nutné provést ručně.</span><span class="sxs-lookup"><span data-stu-id="cd2b9-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="cd2b9-109">Příznaky, které se mají předat podél [openscope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="cd2b9-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="cd2b9-110">Přijímá ID importovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="cd2b9-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="cd2b9-111">Přijímá obor importu sestavení [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cd2b9-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="cd2b9-112">Je nastavena na hodnotu NULL, pokud není soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="cd2b9-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="cd2b9-113">Získá počet importovaných souborů a/nebo obory.</span><span class="sxs-lookup"><span data-stu-id="cd2b9-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd2b9-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cd2b9-114">Return Value</span></span>  
 <span data-ttu-id="cd2b9-115">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="cd2b9-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd2b9-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd2b9-116">Requirements</span></span>  
 <span data-ttu-id="cd2b9-117">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="cd2b9-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2b9-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd2b9-118">See also</span></span>

- [<span data-ttu-id="cd2b9-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd2b9-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="cd2b9-120">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd2b9-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="cd2b9-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="cd2b9-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
