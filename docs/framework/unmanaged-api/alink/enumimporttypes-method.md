---
title: EnumImportTypes – metoda
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90319886dfe149a3d2d76451c1a8526299cf5b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401645"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="fd05c-102">EnumImportTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="fd05c-102">EnumImportTypes Method</span></span>
<span data-ttu-id="fd05c-103">Vytvoří výčet jednotlivých typů v každém oboru.</span><span class="sxs-lookup"><span data-stu-id="fd05c-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd05c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd05c-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd05c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd05c-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="fd05c-106">Obslužná rutina pro enumerátor.</span><span class="sxs-lookup"><span data-stu-id="fd05c-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="fd05c-107">Maximální počet typů, který chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="fd05c-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="fd05c-108">Recieves zadejte tokeny nepřesahující `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="fd05c-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="fd05c-109">Získá skutečný počet typu v `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="fd05c-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd05c-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fd05c-110">Return Value</span></span>  
 <span data-ttu-id="fd05c-111">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="fd05c-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd05c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd05c-112">Requirements</span></span>  
 <span data-ttu-id="fd05c-113">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="fd05c-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd05c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd05c-114">See Also</span></span>  
 [<span data-ttu-id="fd05c-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd05c-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="fd05c-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd05c-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="fd05c-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="fd05c-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
