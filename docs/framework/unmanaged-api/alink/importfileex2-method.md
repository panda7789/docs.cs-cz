---
title: "ImportFileEx2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 78ed173e795b875a171edd8ce49b11df49570827
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="importfileex2-method"></a><span data-ttu-id="200a1-102">ImportFileEx2 – metoda</span><span class="sxs-lookup"><span data-stu-id="200a1-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="200a1-103">Importuje sestavení a nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="200a1-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="200a1-104">Tato metoda je jako [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale funguje i v případě, že importovaný soubor neexistuje na disku.</span><span class="sxs-lookup"><span data-stu-id="200a1-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="200a1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="200a1-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="200a1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="200a1-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="200a1-107">Název soubor pro import.</span><span class="sxs-lookup"><span data-stu-id="200a1-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="200a1-108">Nepovinný název cílového souboru.</span><span class="sxs-lookup"><span data-stu-id="200a1-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="200a1-109">Volitelné import oboru [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="200a1-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="200a1-110">V případě hodnoty TRUE je používán importtypes –, jinak se import se musí provádět ručně.</span><span class="sxs-lookup"><span data-stu-id="200a1-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="200a1-111">Příznaky tak, aby se předají [openscope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="200a1-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="200a1-112">Získá jedinečné ID pro sestavení, nebo soubor.</span><span class="sxs-lookup"><span data-stu-id="200a1-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="200a1-113">Obdrží sestavení import oboru [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="200a1-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="200a1-114">Může mít hodnotu NULL, pokud soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="200a1-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="200a1-115">Získá počet souborů a/nebo obory importovat.</span><span class="sxs-lookup"><span data-stu-id="200a1-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="200a1-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="200a1-116">Return Value</span></span>  
 <span data-ttu-id="200a1-117">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="200a1-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="200a1-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="200a1-118">Requirements</span></span>  
 <span data-ttu-id="200a1-119">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="200a1-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="200a1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="200a1-120">See Also</span></span>  
 [<span data-ttu-id="200a1-121">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="200a1-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="200a1-122">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="200a1-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="200a1-123">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="200a1-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
