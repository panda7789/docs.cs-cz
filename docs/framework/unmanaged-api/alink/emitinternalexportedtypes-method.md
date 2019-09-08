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
ms.openlocfilehash: 04103ad305e0ae97669f3e07e06f03c2cdb4dfbd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787517"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="62d66-102">EmitInternalExportedTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="62d66-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="62d66-103">Vygeneruje typy přidané do sestavení.</span><span class="sxs-lookup"><span data-stu-id="62d66-103">Emits types added to the assembly.</span></span> <span data-ttu-id="62d66-104">Tuto metodu volejte po přidání známých vnitřních typů.</span><span class="sxs-lookup"><span data-stu-id="62d66-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62d66-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62d66-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="62d66-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="62d66-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="62d66-107">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="62d66-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62d66-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="62d66-108">Return Value</span></span>  
 <span data-ttu-id="62d66-109">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="62d66-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62d66-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62d66-110">Requirements</span></span>  
 <span data-ttu-id="62d66-111">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="62d66-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d66-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62d66-112">See also</span></span>

- [<span data-ttu-id="62d66-113">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62d66-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="62d66-114">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62d66-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="62d66-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="62d66-115">ALink API</span></span>](index.md)
