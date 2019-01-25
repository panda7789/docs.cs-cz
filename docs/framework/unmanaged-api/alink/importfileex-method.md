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
ms.openlocfilehash: a0381ee61a0128a8ae303d44198f8d391b4531a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660616"
---
# <a name="importfileex-method"></a><span data-ttu-id="02a88-102">ImportFileEx – metoda</span><span class="sxs-lookup"><span data-stu-id="02a88-102">ImportFileEx Method</span></span>
<span data-ttu-id="02a88-103">Importy určili sestavení nebo nevázaného modulu.</span><span class="sxs-lookup"><span data-stu-id="02a88-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02a88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02a88-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="02a88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02a88-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="02a88-106">Plně kvalifikovaný název souboru, ze kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="02a88-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="02a88-107">Volitelný název cílového souboru.</span><span class="sxs-lookup"><span data-stu-id="02a88-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="02a88-108">Při hodnotě TRUE se používá importtypes –, jinak se import je nutné provést ručně.</span><span class="sxs-lookup"><span data-stu-id="02a88-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="02a88-109">Příznaky, které se mají předat podél [openscope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="02a88-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="02a88-110">Přijímá ID importovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="02a88-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="02a88-111">Přijímá obor importu sestavení [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="02a88-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="02a88-112">Je nastavena na hodnotu NULL, pokud není soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="02a88-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="02a88-113">Získá počet importovaných souborů a/nebo obory.</span><span class="sxs-lookup"><span data-stu-id="02a88-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02a88-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="02a88-114">Return Value</span></span>  
 <span data-ttu-id="02a88-115">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="02a88-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02a88-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02a88-116">Requirements</span></span>  
 <span data-ttu-id="02a88-117">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="02a88-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a88-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02a88-118">See also</span></span>
- [<span data-ttu-id="02a88-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02a88-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="02a88-120">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02a88-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="02a88-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="02a88-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
