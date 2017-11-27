---
title: "ImportFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile
helpviewer_keywords: ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 46830699ba43c406da313653e1910e8f7a18a2ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="importfile-method"></a><span data-ttu-id="0ec6d-102">ImportFile – metoda</span><span class="sxs-lookup"><span data-stu-id="0ec6d-102">ImportFile Method</span></span>
<span data-ttu-id="0ec6d-103">Importuje sestavení a nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="0ec6d-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ec6d-104">Syntax</span></span>  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ec6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ec6d-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="0ec6d-106">Plně kvalifikovaný název soubor pro import.</span><span class="sxs-lookup"><span data-stu-id="0ec6d-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="0ec6d-107">Název souboru volitelný výstup, který slouží k přejmenování souboru, jako je propojena do sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ec6d-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="0ec6d-108">V případě hodnoty TRUE je používán importtypes –, jinak se import se musí provádět ručně.</span><span class="sxs-lookup"><span data-stu-id="0ec6d-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="0ec6d-109">Ukazatel na token, kde bude uložen soubor jedinečné ID.</span><span class="sxs-lookup"><span data-stu-id="0ec6d-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="0ec6d-110">Soubor může být sestavení nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="0ec6d-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="0ec6d-111">Obdrží ukazatel na [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0ec6d-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="0ec6d-112">Může mít hodnotu NULL, pokud soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ec6d-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="0ec6d-113">Ukazatel na počet soubory nebo obory, které byly naimportovány.</span><span class="sxs-lookup"><span data-stu-id="0ec6d-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ec6d-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0ec6d-114">Return Value</span></span>  
 <span data-ttu-id="0ec6d-115">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="0ec6d-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ec6d-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ec6d-116">Requirements</span></span>  
 <span data-ttu-id="0ec6d-117">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="0ec6d-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ec6d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ec6d-118">See Also</span></span>  
 [<span data-ttu-id="0ec6d-119">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ec6d-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="0ec6d-120">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ec6d-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="0ec6d-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="0ec6d-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
