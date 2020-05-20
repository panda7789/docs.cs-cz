---
title: ISymUnmanagedConstant::GetValue – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
ms.openlocfilehash: 8e20d2e0f3d5cb6dc7444c8e78665b6c8b82d2de
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441471"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="b7fec-102">ISymUnmanagedConstant::GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b7fec-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="b7fec-103">Získá hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="b7fec-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7fec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7fec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7fec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7fec-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="b7fec-106">mimo Ukazatel na proměnnou, která přijímá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b7fec-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7fec-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b7fec-107">Return Value</span></span>  
 <span data-ttu-id="b7fec-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b7fec-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7fec-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7fec-109">Requirements</span></span>  
 <span data-ttu-id="b7fec-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b7fec-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7fec-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7fec-111">See also</span></span>

- [<span data-ttu-id="b7fec-112">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7fec-112">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="b7fec-113">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="b7fec-113">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="b7fec-114">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="b7fec-114">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
