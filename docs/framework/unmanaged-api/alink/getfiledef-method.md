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
ms.openlocfilehash: 9153c9b3735e265d59ba072f747c92434c95d9ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789867"
---
# <a name="getfiledef-method"></a><span data-ttu-id="1cdb6-102">GetFileDef – metoda</span><span class="sxs-lookup"><span data-stu-id="1cdb6-102">GetFileDef Method</span></span>
<span data-ttu-id="1cdb6-103">Získá skutečný FileDef tokenu používaného v metadatech (na rozdíl od token přiřadil ALink).</span><span class="sxs-lookup"><span data-stu-id="1cdb6-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cdb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cdb6-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cdb6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1cdb6-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1cdb6-106">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="1cdb6-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="1cdb6-107">Token přidaný soubor jako získaných AddFile – metoda nebo addimport – metoda.</span><span class="sxs-lookup"><span data-stu-id="1cdb6-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="1cdb6-108">Přijme FileDef token.</span><span class="sxs-lookup"><span data-stu-id="1cdb6-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cdb6-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1cdb6-109">Return Value</span></span>  
 <span data-ttu-id="1cdb6-110">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="1cdb6-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cdb6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1cdb6-111">Requirements</span></span>  
 <span data-ttu-id="1cdb6-112">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="1cdb6-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cdb6-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1cdb6-113">See also</span></span>

- [<span data-ttu-id="1cdb6-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1cdb6-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="1cdb6-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1cdb6-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="1cdb6-116">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="1cdb6-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
