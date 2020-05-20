---
title: ISymUnmanagedScope::GetEndOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: 4d6bd239a15bd196f840007af120cb062499f4c9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614848"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="dd8b9-102">ISymUnmanagedScope::GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="dd8b9-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="dd8b9-103">Získá posunutí konce tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="dd8b9-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd8b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd8b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd8b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd8b9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="dd8b9-106">mimo Ukazatel na `ULONG32` , který obdrží koncový posun.</span><span class="sxs-lookup"><span data-stu-id="dd8b9-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd8b9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dd8b9-107">Return Value</span></span>  
 <span data-ttu-id="dd8b9-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="dd8b9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd8b9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd8b9-109">Requirements</span></span>  
 <span data-ttu-id="dd8b9-110">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dd8b9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8b9-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd8b9-111">See also</span></span>

- [<span data-ttu-id="dd8b9-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd8b9-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="dd8b9-113">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="dd8b9-113">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)
