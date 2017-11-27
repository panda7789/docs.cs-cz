---
title: "ImportFileEx2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportFileEx2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFileEx2
helpviewer_keywords: ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2416a630f9bd763d4d4d31170cc606b160bb854
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="importfileex2-method"></a><span data-ttu-id="e0c24-102">ImportFileEx2 – metoda</span><span class="sxs-lookup"><span data-stu-id="e0c24-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="e0c24-103">Importuje sestavení a nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="e0c24-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="e0c24-104">Tato metoda je jako [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale funguje i v případě, že importovaný soubor neexistuje na disku.</span><span class="sxs-lookup"><span data-stu-id="e0c24-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0c24-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0c24-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="e0c24-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0c24-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="e0c24-107">Název soubor pro import.</span><span class="sxs-lookup"><span data-stu-id="e0c24-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="e0c24-108">Nepovinný název cílového souboru.</span><span class="sxs-lookup"><span data-stu-id="e0c24-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="e0c24-109">Volitelné import oboru [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e0c24-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="e0c24-110">V případě hodnoty TRUE je používán importtypes –, jinak se import se musí provádět ručně.</span><span class="sxs-lookup"><span data-stu-id="e0c24-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="e0c24-111">Příznaky tak, aby se předají [openscope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="e0c24-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="e0c24-112">Získá jedinečné ID pro sestavení, nebo soubor.</span><span class="sxs-lookup"><span data-stu-id="e0c24-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="e0c24-113">Obdrží sestavení import oboru [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e0c24-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="e0c24-114">Může mít hodnotu NULL, pokud soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="e0c24-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="e0c24-115">Získá počet souborů a/nebo obory importovat.</span><span class="sxs-lookup"><span data-stu-id="e0c24-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0c24-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e0c24-116">Return Value</span></span>  
 <span data-ttu-id="e0c24-117">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e0c24-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0c24-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0c24-118">Requirements</span></span>  
 <span data-ttu-id="e0c24-119">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="e0c24-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c24-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0c24-120">See Also</span></span>  
 [<span data-ttu-id="e0c24-121">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0c24-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e0c24-122">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0c24-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e0c24-123">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="e0c24-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
