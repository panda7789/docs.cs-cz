---
title: ImportFileEx2 – metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d09877d9ca8dde601d2b515bce63bfdca53b6ab0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498130"
---
# <a name="importfileex2-method"></a><span data-ttu-id="c70f2-102">ImportFileEx2 – metoda</span><span class="sxs-lookup"><span data-stu-id="c70f2-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="c70f2-103">Importuje nevázaného modulů a sestavení.</span><span class="sxs-lookup"><span data-stu-id="c70f2-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="c70f2-104">Tato metoda je jako [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale funguje i v případě, že importovaný soubor buď neexistuje na disku.</span><span class="sxs-lookup"><span data-stu-id="c70f2-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c70f2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c70f2-105">Syntax</span></span>  
  
```  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c70f2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c70f2-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="c70f2-107">Název souboru k importu.</span><span class="sxs-lookup"><span data-stu-id="c70f2-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="c70f2-108">Volitelný název cílového souboru.</span><span class="sxs-lookup"><span data-stu-id="c70f2-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="c70f2-109">Volitelný import oboru [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c70f2-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="c70f2-110">Při hodnotě TRUE se používá importtypes –, jinak se import je nutné provést ručně.</span><span class="sxs-lookup"><span data-stu-id="c70f2-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="c70f2-111">Příznaky, které se mají předat podél [openscope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="c70f2-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="c70f2-112">Získá jedinečný ID pro sestavení nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="c70f2-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="c70f2-113">Přijímá obor importu sestavení [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c70f2-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="c70f2-114">Může mít hodnotu NULL, pokud soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="c70f2-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="c70f2-115">Získá počet souborů a/nebo importovat obory.</span><span class="sxs-lookup"><span data-stu-id="c70f2-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c70f2-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c70f2-116">Return Value</span></span>  
 <span data-ttu-id="c70f2-117">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="c70f2-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c70f2-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c70f2-118">Requirements</span></span>  
 <span data-ttu-id="c70f2-119">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="c70f2-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70f2-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c70f2-120">See also</span></span>
- [<span data-ttu-id="c70f2-121">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c70f2-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c70f2-122">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c70f2-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c70f2-123">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="c70f2-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
