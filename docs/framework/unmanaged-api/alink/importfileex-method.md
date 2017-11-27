---
title: "ImportFileEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportFileEx
api_location: alink.dll
api_type: COM
f1_keywords: ImportFileEx
helpviewer_keywords: ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71a7bc1ba9f23f1c581ca3528752e04003d9857c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="importfileex-method"></a><span data-ttu-id="ba163-102">ImportFileEx – metoda</span><span class="sxs-lookup"><span data-stu-id="ba163-102">ImportFileEx Method</span></span>
<span data-ttu-id="ba163-103">Importy uvedené nevázaný modul nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba163-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba163-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba163-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ba163-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba163-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="ba163-106">Plně kvalifikovaný název souboru, ze kterých chcete importovat.</span><span class="sxs-lookup"><span data-stu-id="ba163-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="ba163-107">Nepovinný název cílového souboru.</span><span class="sxs-lookup"><span data-stu-id="ba163-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="ba163-108">V případě hodnoty TRUE je používán importtypes –, jinak se import se musí provádět ručně.</span><span class="sxs-lookup"><span data-stu-id="ba163-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="ba163-109">Příznaky tak, aby se předají [openscope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="ba163-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="ba163-110">Získá ID importovaný soubor.</span><span class="sxs-lookup"><span data-stu-id="ba163-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="ba163-111">Obdrží sestavení import oboru [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ba163-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="ba163-112">Je nastavena na hodnotu NULL, pokud není soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba163-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="ba163-113">Získá počet importovaných souborů nebo obory.</span><span class="sxs-lookup"><span data-stu-id="ba163-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba163-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ba163-114">Return Value</span></span>  
 <span data-ttu-id="ba163-115">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ba163-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba163-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba163-116">Requirements</span></span>  
 <span data-ttu-id="ba163-117">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="ba163-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba163-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba163-118">See Also</span></span>  
 [<span data-ttu-id="ba163-119">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba163-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ba163-120">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba163-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ba163-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="ba163-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
