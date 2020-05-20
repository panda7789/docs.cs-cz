---
title: ISymUnmanagedScope::GetLocalCount – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
ms.openlocfilehash: 9ffba23e3821c48c9b0708e4b6b617db4ddc5959
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83611260"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="fdd40-102">ISymUnmanagedScope::GetLocalCount – metoda</span><span class="sxs-lookup"><span data-stu-id="fdd40-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="fdd40-103">Získá počet místních proměnných definovaných v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="fdd40-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdd40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdd40-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdd40-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdd40-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fdd40-106">mimo Ukazatel na `ULONG32` , který přijímá počet místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="fdd40-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdd40-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fdd40-107">Return Value</span></span>  
 <span data-ttu-id="fdd40-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fdd40-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdd40-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdd40-109">Requirements</span></span>  
 <span data-ttu-id="fdd40-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fdd40-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd40-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdd40-111">See also</span></span>

- [<span data-ttu-id="fdd40-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdd40-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
