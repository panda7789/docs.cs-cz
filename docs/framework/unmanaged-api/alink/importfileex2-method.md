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
ms.openlocfilehash: 784e58e0c5c2329705671580d53763f2ac30f0b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201348"
---
# <a name="importfileex2-method"></a><span data-ttu-id="68dac-102">ImportFileEx2 – metoda</span><span class="sxs-lookup"><span data-stu-id="68dac-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="68dac-103">Importuje nevázaného modulů a sestavení.</span><span class="sxs-lookup"><span data-stu-id="68dac-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="68dac-104">Tato metoda je jako [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale funguje i v případě, že importovaný soubor buď neexistuje na disku.</span><span class="sxs-lookup"><span data-stu-id="68dac-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68dac-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68dac-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="68dac-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="68dac-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="68dac-107">Název souboru k importu.</span><span class="sxs-lookup"><span data-stu-id="68dac-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="68dac-108">Volitelný název cílového souboru.</span><span class="sxs-lookup"><span data-stu-id="68dac-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="68dac-109">Volitelný import oboru [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="68dac-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="68dac-110">Při hodnotě TRUE se používá importtypes –, jinak se import je nutné provést ručně.</span><span class="sxs-lookup"><span data-stu-id="68dac-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="68dac-111">Příznaky, které se mají předat podél [openscope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="68dac-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="68dac-112">Získá jedinečný ID pro sestavení nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="68dac-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="68dac-113">Přijímá obor importu sestavení [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="68dac-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="68dac-114">Může mít hodnotu NULL, pokud soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="68dac-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="68dac-115">Získá počet souborů a/nebo importovat obory.</span><span class="sxs-lookup"><span data-stu-id="68dac-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68dac-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="68dac-116">Return Value</span></span>  
 <span data-ttu-id="68dac-117">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="68dac-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68dac-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68dac-118">Requirements</span></span>  
 <span data-ttu-id="68dac-119">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="68dac-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68dac-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68dac-120">See also</span></span>

- [<span data-ttu-id="68dac-121">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68dac-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="68dac-122">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68dac-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="68dac-123">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="68dac-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
