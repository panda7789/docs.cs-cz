---
title: ISymUnmanagedReader::GetVariables – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
ms.openlocfilehash: 4590d2734ea89bc1bc8a30db1c7ecac5effafd7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429754"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="4ea01-102">ISymUnmanagedReader::GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="4ea01-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="4ea01-103">Vrátí nemístní proměnnou, která je dána jejím nadřazeným a názvem.</span><span class="sxs-lookup"><span data-stu-id="4ea01-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ea01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ea01-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ea01-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ea01-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="4ea01-106">pro Nadřazená proměnná proměnné.</span><span class="sxs-lookup"><span data-stu-id="4ea01-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="4ea01-107">pro Velikost pole `pVars`.</span><span class="sxs-lookup"><span data-stu-id="4ea01-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="4ea01-108">mimo Ukazatel na proměnnou, která přijímá počet proměnných vrácených v `pVars`.</span><span class="sxs-lookup"><span data-stu-id="4ea01-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="4ea01-109">mimo Ukazatel na proměnnou, která přijímá proměnné.</span><span class="sxs-lookup"><span data-stu-id="4ea01-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ea01-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4ea01-110">Return Value</span></span>  
 <span data-ttu-id="4ea01-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4ea01-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ea01-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ea01-112">Requirements</span></span>  
 <span data-ttu-id="4ea01-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4ea01-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea01-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ea01-114">See also</span></span>

- [<span data-ttu-id="4ea01-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ea01-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
