---
title: ISymUnmanagedVariable::GetName – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
ms.openlocfilehash: 77dec4332aa65f6125685db607169b3398bcab98
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446052"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="94079-102">ISymUnmanagedVariable::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="94079-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="94079-103">Gets the name of this variable.</span><span class="sxs-lookup"><span data-stu-id="94079-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94079-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94079-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94079-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94079-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="94079-106">[in] The length of the buffer that the `pcchName` parameter points to.</span><span class="sxs-lookup"><span data-stu-id="94079-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="94079-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span><span class="sxs-lookup"><span data-stu-id="94079-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="94079-108">[out] The buffer that stores the name.</span><span class="sxs-lookup"><span data-stu-id="94079-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94079-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="94079-109">Return Value</span></span>  
 <span data-ttu-id="94079-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="94079-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94079-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94079-111">Requirements</span></span>  
 <span data-ttu-id="94079-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="94079-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94079-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94079-113">See also</span></span>

- [<span data-ttu-id="94079-114">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="94079-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
