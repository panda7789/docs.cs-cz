---
title: ImportFile – metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d76e9b4e18b46d0b546d6c66fa572c35cb9fcefe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741778"
---
# <a name="importfile-method"></a><span data-ttu-id="60464-102">ImportFile – metoda</span><span class="sxs-lookup"><span data-stu-id="60464-102">ImportFile Method</span></span>
<span data-ttu-id="60464-103">Importuje nevázaného modulů a sestavení.</span><span class="sxs-lookup"><span data-stu-id="60464-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60464-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60464-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="60464-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60464-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="60464-106">Plně kvalifikovaný název souboru k importu.</span><span class="sxs-lookup"><span data-stu-id="60464-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="60464-107">Volitelné výstupní název souboru, který slouží k přejmenování souboru, jako je propojený do sestavení.</span><span class="sxs-lookup"><span data-stu-id="60464-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="60464-108">Při hodnotě TRUE se používá importtypes –, jinak se import je nutné provést ručně.</span><span class="sxs-lookup"><span data-stu-id="60464-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="60464-109">Ukazatel na token, kam se budou ukládat jedinečný Identifikátor souboru.</span><span class="sxs-lookup"><span data-stu-id="60464-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="60464-110">Soubor může být sestavení nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="60464-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="60464-111">Přijímá ukazatel na [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="60464-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="60464-112">Může mít hodnotu NULL, pokud soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="60464-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="60464-113">Ukazatel na počet souborů a/nebo obory, které byly naimportovány.</span><span class="sxs-lookup"><span data-stu-id="60464-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60464-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="60464-114">Return Value</span></span>  
 <span data-ttu-id="60464-115">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="60464-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60464-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60464-116">Requirements</span></span>  
 <span data-ttu-id="60464-117">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="60464-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60464-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60464-118">See also</span></span>

- [<span data-ttu-id="60464-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60464-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="60464-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60464-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="60464-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="60464-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
