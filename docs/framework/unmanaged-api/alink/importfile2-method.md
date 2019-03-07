---
title: ImportFile2 – metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 88006703ba4a491ae458868a1431be618d37252a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471196"
---
# <a name="importfile2-method"></a><span data-ttu-id="7b1aa-102">ImportFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="7b1aa-102">ImportFile2 Method</span></span>
<span data-ttu-id="7b1aa-103">Importuje nevázaného modulů a sestavení.</span><span class="sxs-lookup"><span data-stu-id="7b1aa-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="7b1aa-104">Tato metoda je jako [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale funguje i v případě, že importovaný soubor buď neexistuje na disku.</span><span class="sxs-lookup"><span data-stu-id="7b1aa-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b1aa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b1aa-105">Syntax</span></span>  
  
```  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b1aa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b1aa-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="7b1aa-107">Název souboru k importu.</span><span class="sxs-lookup"><span data-stu-id="7b1aa-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="7b1aa-108">Volitelné výstupní název souboru, který slouží k přejmenování souboru, jako je propojený do sestavení.</span><span class="sxs-lookup"><span data-stu-id="7b1aa-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="7b1aa-109">Volitelné oboru [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7b1aa-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="7b1aa-110">Při hodnotě TRUE se používá importtypes –, jinak se import je nutné provést ručně.</span><span class="sxs-lookup"><span data-stu-id="7b1aa-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="7b1aa-111">Přijímá ID pro soubor nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="7b1aa-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="7b1aa-112">Přijímá [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7b1aa-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="7b1aa-113">Hodnota NULL, pokud soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="7b1aa-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="7b1aa-114">Přijímá soubory a/nebo importovat obory nenašel.</span><span class="sxs-lookup"><span data-stu-id="7b1aa-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b1aa-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7b1aa-115">Return Value</span></span>  
 <span data-ttu-id="7b1aa-116">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="7b1aa-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b1aa-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b1aa-117">Requirements</span></span>  
 <span data-ttu-id="7b1aa-118">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="7b1aa-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b1aa-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b1aa-119">See also</span></span>
- [<span data-ttu-id="7b1aa-120">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b1aa-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="7b1aa-121">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b1aa-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="7b1aa-122">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="7b1aa-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
