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
ms.openlocfilehash: b48d131fa99b65d38856d2b635bf59145db9157e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615238"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="87f37-102">ISymUnmanagedVariable::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="87f37-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="87f37-103">Získá název této proměnné.</span><span class="sxs-lookup"><span data-stu-id="87f37-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87f37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87f37-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87f37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87f37-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="87f37-106">pro Délka vyrovnávací paměti, `pcchName` na kterou parametr odkazuje.</span><span class="sxs-lookup"><span data-stu-id="87f37-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="87f37-107">mimo Ukazatel na `ULONG32` , který obdrží velikost vyrovnávací paměti, která je nutná k omezení názvu, včetně ukončení hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="87f37-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="87f37-108">mimo Vyrovnávací paměť, která ukládá název.</span><span class="sxs-lookup"><span data-stu-id="87f37-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87f37-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="87f37-109">Return Value</span></span>  
 <span data-ttu-id="87f37-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="87f37-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87f37-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87f37-111">Requirements</span></span>  
 <span data-ttu-id="87f37-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="87f37-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f37-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="87f37-113">See also</span></span>

- [<span data-ttu-id="87f37-114">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87f37-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
