---
title: AddFile Method1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.AddFile
- AddFile
api_location: alink.dll
api_type: COM
f1_keywords: AddFile
helpviewer_keywords: AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9463f2c41f56287ebfc4fb55aa8208c37522a57f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="addfile-method1"></a><span data-ttu-id="9d51f-102">AddFile Method1</span><span class="sxs-lookup"><span data-stu-id="9d51f-102">AddFile Method1</span></span>
<span data-ttu-id="9d51f-103">Přidá soubory do sestavení.</span><span class="sxs-lookup"><span data-stu-id="9d51f-103">Adds files to the assembly.</span></span> <span data-ttu-id="9d51f-104">Můžete také použít k vytvoření nepřipojeného moduly.</span><span class="sxs-lookup"><span data-stu-id="9d51f-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d51f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d51f-105">Syntax</span></span>  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d51f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d51f-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9d51f-107">Jedinečné ID sestavení, které má být rozšířen.</span><span class="sxs-lookup"><span data-stu-id="9d51f-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="9d51f-108">Plně kvalifikovaný název souboru, který se má přidat.</span><span class="sxs-lookup"><span data-stu-id="9d51f-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9d51f-109">Modelu COM + FileDef flags – například `ffContainsNoMetaData` a `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="9d51f-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="9d51f-110">`dwFlags`Předaný [definefile – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="9d51f-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="9d51f-111">[Imetadataemit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) rozhraní, který se má použít pro vydávání metadata, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="9d51f-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="9d51f-112">Ukazatel na uložení jedinečné ID přidaný soubor.</span><span class="sxs-lookup"><span data-stu-id="9d51f-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d51f-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9d51f-113">Return Value</span></span>  
 <span data-ttu-id="9d51f-114">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9d51f-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d51f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d51f-115">Requirements</span></span>  
 <span data-ttu-id="9d51f-116">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="9d51f-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d51f-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d51f-117">See Also</span></span>  
 [<span data-ttu-id="9d51f-118">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d51f-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="9d51f-119">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d51f-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="9d51f-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="9d51f-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
