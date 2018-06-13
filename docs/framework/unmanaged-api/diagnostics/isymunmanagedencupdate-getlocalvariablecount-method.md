---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7d557e2111a26c0865c20d8eb952c4d42b5604e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436056"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="07397-102">ISymUnmanagedENCUpdate::GetLocalVariableCount – metoda</span><span class="sxs-lookup"><span data-stu-id="07397-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="07397-103">Získá počet lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="07397-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07397-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07397-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07397-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07397-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="07397-106">[v] Metadata token metod.</span><span class="sxs-lookup"><span data-stu-id="07397-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="07397-107">[out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat číslo lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="07397-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07397-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="07397-108">Return Value</span></span>  
 <span data-ttu-id="07397-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="07397-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07397-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="07397-110">Requirements</span></span>  
 <span data-ttu-id="07397-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="07397-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07397-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="07397-112">See Also</span></span>  
 [<span data-ttu-id="07397-113">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="07397-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
