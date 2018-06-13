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
ms.openlocfilehash: 61bc7783823408164ae2b073e097a0e85e193be6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401239"
---
# <a name="importfile2-method"></a><span data-ttu-id="f2a71-102">ImportFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="f2a71-102">ImportFile2 Method</span></span>
<span data-ttu-id="f2a71-103">Importuje sestavení a nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="f2a71-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="f2a71-104">Tato metoda je jako [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale funguje i v případě, že importovaný soubor neexistuje na disku.</span><span class="sxs-lookup"><span data-stu-id="f2a71-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a71-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2a71-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f2a71-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2a71-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="f2a71-107">Název soubor pro import.</span><span class="sxs-lookup"><span data-stu-id="f2a71-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="f2a71-108">Název souboru volitelný výstup, který slouží k přejmenování souboru, jako je propojena do sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2a71-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="f2a71-109">Volitelné oboru [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f2a71-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="f2a71-110">V případě hodnoty TRUE je používán importtypes –, jinak se import se musí provádět ručně.</span><span class="sxs-lookup"><span data-stu-id="f2a71-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="f2a71-111">Získá ID pro soubor nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2a71-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="f2a71-112">Přijme [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f2a71-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="f2a71-113">Hodnota NULL, pokud soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2a71-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="f2a71-114">Obdrží nalezen soubory nebo obory importovat.</span><span class="sxs-lookup"><span data-stu-id="f2a71-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2a71-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f2a71-115">Return Value</span></span>  
 <span data-ttu-id="f2a71-116">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f2a71-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2a71-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2a71-117">Requirements</span></span>  
 <span data-ttu-id="f2a71-118">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="f2a71-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a71-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2a71-119">See Also</span></span>  
 [<span data-ttu-id="f2a71-120">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2a71-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f2a71-121">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2a71-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f2a71-122">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="f2a71-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
