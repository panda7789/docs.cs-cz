---
title: "GetFileDef – metoda"
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
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 473cbaba8712ee247733ba3075c0163e259cf4dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getfiledef-method"></a><span data-ttu-id="ddd9c-102">GetFileDef – metoda</span><span class="sxs-lookup"><span data-stu-id="ddd9c-102">GetFileDef Method</span></span>
<span data-ttu-id="ddd9c-103">Načte skutečné FileDef tokenu používaného v metadatech (na rozdíl od token přiřadila ALink).</span><span class="sxs-lookup"><span data-stu-id="ddd9c-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddd9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddd9c-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddd9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddd9c-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ddd9c-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="ddd9c-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="ddd9c-107">Token souboru přidané jako načítají AddFile – metoda nebo addimport – metoda.</span><span class="sxs-lookup"><span data-stu-id="ddd9c-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="ddd9c-108">Přijme FileDef token.</span><span class="sxs-lookup"><span data-stu-id="ddd9c-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddd9c-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ddd9c-109">Return Value</span></span>  
 <span data-ttu-id="ddd9c-110">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ddd9c-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddd9c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ddd9c-111">Requirements</span></span>  
 <span data-ttu-id="ddd9c-112">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="ddd9c-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd9c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddd9c-113">See Also</span></span>  
 [<span data-ttu-id="ddd9c-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddd9c-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ddd9c-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddd9c-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ddd9c-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="ddd9c-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
