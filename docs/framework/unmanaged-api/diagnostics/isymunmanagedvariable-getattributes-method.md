---
title: ISymUnmanagedVariable::GetAttributes – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
ms.openlocfilehash: 29869abdd39f61c6c9cb51d6b2be50fa462c5b70
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615251"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="beec8-102">ISymUnmanagedVariable::GetAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="beec8-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="beec8-103">Získá příznaky atributu pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="beec8-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beec8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="beec8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="beec8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="beec8-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="beec8-106">mimo Ukazatel na `ULONG32` , který přijímá atributy.</span><span class="sxs-lookup"><span data-stu-id="beec8-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="beec8-107">Vrácená hodnota bude jedna z hodnot definovaných ve výčtu [CorSymVarFlag –](corsymvarflag-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="beec8-107">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="beec8-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="beec8-108">Return Value</span></span>  
 <span data-ttu-id="beec8-109">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="beec8-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beec8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="beec8-110">Requirements</span></span>  
 <span data-ttu-id="beec8-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="beec8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beec8-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="beec8-112">See also</span></span>

- [<span data-ttu-id="beec8-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="beec8-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
