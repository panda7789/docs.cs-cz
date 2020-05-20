---
title: ISymUnmanagedReader::GetGlobalVariables – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
ms.openlocfilehash: 20bfb3e48f411524bd4d9798f17dd935595a12bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615017"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="c1c0f-102">ISymUnmanagedReader::GetGlobalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="c1c0f-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="c1c0f-103">Vrátí všechny globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="c1c0f-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1c0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1c0f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1c0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1c0f-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="c1c0f-106">pro Délka vyrovnávací paměti, na kterou ukazuje `pcVars` .</span><span class="sxs-lookup"><span data-stu-id="c1c0f-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="c1c0f-107">mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti vyžadované k omezení proměnných.</span><span class="sxs-lookup"><span data-stu-id="c1c0f-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="c1c0f-108">mimo Vyrovnávací paměť obsahující proměnné.</span><span class="sxs-lookup"><span data-stu-id="c1c0f-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1c0f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c1c0f-109">Return Value</span></span>  
 <span data-ttu-id="c1c0f-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c1c0f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1c0f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1c0f-111">Requirements</span></span>  
 <span data-ttu-id="c1c0f-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c1c0f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c0f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1c0f-113">See also</span></span>

- [<span data-ttu-id="c1c0f-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1c0f-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
