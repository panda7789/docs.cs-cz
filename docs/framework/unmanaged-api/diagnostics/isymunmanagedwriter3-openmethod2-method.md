---
title: ISymUnmanagedWriter3::OpenMethod2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: 0c112819ef3bc4f9a7146ee80f55202ff89d689a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178319"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="7f1e4-102">ISymUnmanagedWriter3::OpenMethod2 – metoda</span><span class="sxs-lookup"><span data-stu-id="7f1e4-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="7f1e4-103">Otevře metodu a v obraze poskytuje její skutečný posun oddílu.</span><span class="sxs-lookup"><span data-stu-id="7f1e4-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f1e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f1e4-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f1e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f1e4-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="7f1e4-106">[v] Token metadat pro metodu, která má být otevřena.</span><span class="sxs-lookup"><span data-stu-id="7f1e4-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="7f1e4-107">[v] Posun oddílu v obraze.</span><span class="sxs-lookup"><span data-stu-id="7f1e4-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="7f1e4-108">[v] Posun v obraze.</span><span class="sxs-lookup"><span data-stu-id="7f1e4-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f1e4-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7f1e4-109">Return Value</span></span>  
 <span data-ttu-id="7f1e4-110">S_OK pokud je metoda úspěšná; v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7f1e4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f1e4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f1e4-111">Requirements</span></span>  
 <span data-ttu-id="7f1e4-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7f1e4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f1e4-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f1e4-113">See also</span></span>

- [<span data-ttu-id="7f1e4-114">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f1e4-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="7f1e4-115">OpenMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="7f1e4-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
