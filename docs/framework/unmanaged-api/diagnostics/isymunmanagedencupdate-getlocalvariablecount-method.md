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
ms.openlocfilehash: d04c9865d8272bf8d04080f6049ddfb1d4c643bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614575"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="015b1-102">ISymUnmanagedENCUpdate::GetLocalVariableCount – metoda</span><span class="sxs-lookup"><span data-stu-id="015b1-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="015b1-103">Získá počet místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="015b1-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="015b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="015b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="015b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="015b1-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="015b1-106">pro Token metadat metod.</span><span class="sxs-lookup"><span data-stu-id="015b1-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="015b1-107">mimo Ukazatel na `ULONG32` , který obdrží velikost vyrovnávací paměti, která je nutná k omezení počtu místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="015b1-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="015b1-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="015b1-108">Return Value</span></span>  
 <span data-ttu-id="015b1-109">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="015b1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="015b1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="015b1-110">Requirements</span></span>  
 <span data-ttu-id="015b1-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="015b1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="015b1-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="015b1-112">See also</span></span>

- [<span data-ttu-id="015b1-113">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="015b1-113">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
