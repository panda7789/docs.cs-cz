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
ms.openlocfilehash: 637e1aed003e211654141ab397c9c0b4724753c2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615485"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="d2259-102">ISymUnmanagedReader::GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="d2259-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="d2259-103">Vrátí nemístní proměnnou, která je dána jejím nadřazeným a názvem.</span><span class="sxs-lookup"><span data-stu-id="d2259-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2259-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2259-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2259-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2259-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="d2259-106">pro Nadřazená proměnná proměnné.</span><span class="sxs-lookup"><span data-stu-id="d2259-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="d2259-107">pro Velikost `pVars` pole.</span><span class="sxs-lookup"><span data-stu-id="d2259-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="d2259-108">mimo Ukazatel na proměnnou, která přijímá počet proměnných vrácených v `pVars` .</span><span class="sxs-lookup"><span data-stu-id="d2259-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="d2259-109">mimo Ukazatel na proměnnou, která přijímá proměnné.</span><span class="sxs-lookup"><span data-stu-id="d2259-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2259-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d2259-110">Return Value</span></span>  
 <span data-ttu-id="d2259-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="d2259-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2259-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2259-112">Requirements</span></span>  
 <span data-ttu-id="d2259-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d2259-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2259-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2259-114">See also</span></span>

- [<span data-ttu-id="d2259-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2259-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
