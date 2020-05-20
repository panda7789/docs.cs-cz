---
title: ISymUnmanagedConstant::GetName – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: 2dd70693528904459a34689dbad944c65c971254
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441640"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="c45b7-102">ISymUnmanagedConstant::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="c45b7-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="c45b7-103">Získá název konstanty.</span><span class="sxs-lookup"><span data-stu-id="c45b7-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c45b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c45b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c45b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c45b7-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c45b7-106">pro Délka vyrovnávací paměti, `szName` na kterou parametr odkazuje.</span><span class="sxs-lookup"><span data-stu-id="c45b7-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c45b7-107">mimo Ukazatel na `ULONG32` , který obdrží velikost vyrovnávací paměti, která je nutná k omezení názvu, včetně ukončení hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="c45b7-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="c45b7-108">mimo Vyrovnávací paměť, která ukládá název.</span><span class="sxs-lookup"><span data-stu-id="c45b7-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c45b7-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c45b7-109">Return Value</span></span>  
 <span data-ttu-id="c45b7-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c45b7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c45b7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c45b7-111">Requirements</span></span>  
 <span data-ttu-id="c45b7-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c45b7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c45b7-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c45b7-113">See also</span></span>

- [<span data-ttu-id="c45b7-114">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c45b7-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="c45b7-115">GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="c45b7-115">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="c45b7-116">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c45b7-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
