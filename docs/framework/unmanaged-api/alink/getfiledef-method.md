---
title: GetFileDef – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7cc7b83f7bf1657195778ea38944b2354b09c38
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471339"
---
# <a name="getfiledef-method"></a><span data-ttu-id="eea44-102">GetFileDef – metoda</span><span class="sxs-lookup"><span data-stu-id="eea44-102">GetFileDef Method</span></span>
<span data-ttu-id="eea44-103">Získá skutečný FileDef tokenu používaného v metadatech (na rozdíl od token přiřadil ALink).</span><span class="sxs-lookup"><span data-stu-id="eea44-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eea44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eea44-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="eea44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eea44-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="eea44-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="eea44-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="eea44-107">Token přidaný soubor jako získaných AddFile – metoda nebo addimport – metoda.</span><span class="sxs-lookup"><span data-stu-id="eea44-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="eea44-108">Přijme FileDef token.</span><span class="sxs-lookup"><span data-stu-id="eea44-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eea44-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eea44-109">Return Value</span></span>  
 <span data-ttu-id="eea44-110">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="eea44-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eea44-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eea44-111">Requirements</span></span>  
 <span data-ttu-id="eea44-112">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="eea44-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea44-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eea44-113">See also</span></span>
- [<span data-ttu-id="eea44-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eea44-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="eea44-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eea44-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="eea44-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="eea44-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
