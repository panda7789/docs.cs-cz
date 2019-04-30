---
title: EmitInternalExportedTypes – metoda
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c196bcc159b18b9dc04329d817ebe16e07bb8bb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790010"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="bca51-102">EmitInternalExportedTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="bca51-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="bca51-103">Vysílá typy do sestavení.</span><span class="sxs-lookup"><span data-stu-id="bca51-103">Emits types added to the assembly.</span></span> <span data-ttu-id="bca51-104">Volejte tuto metodu po označuje, že byly přidány vnitřní typy.</span><span class="sxs-lookup"><span data-stu-id="bca51-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca51-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bca51-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="bca51-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bca51-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="bca51-107">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="bca51-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bca51-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bca51-108">Return Value</span></span>  
 <span data-ttu-id="bca51-109">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="bca51-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca51-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bca51-110">Requirements</span></span>  
 <span data-ttu-id="bca51-111">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="bca51-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca51-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bca51-112">See also</span></span>

- [<span data-ttu-id="bca51-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bca51-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="bca51-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bca51-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="bca51-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="bca51-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
