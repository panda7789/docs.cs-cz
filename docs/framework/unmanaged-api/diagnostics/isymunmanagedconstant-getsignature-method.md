---
title: ISymUnmanagedConstant::GetSignature – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
ms.openlocfilehash: 332d60418c744a9391c7c0afc20248c2239b090c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441617"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="fcaf6-102">ISymUnmanagedConstant::GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="fcaf6-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="fcaf6-103">Získá signaturu konstanty.</span><span class="sxs-lookup"><span data-stu-id="fcaf6-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcaf6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcaf6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcaf6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fcaf6-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="fcaf6-106">pro Délka vyrovnávací paměti, `pcSig` na kterou parametr odkazuje.</span><span class="sxs-lookup"><span data-stu-id="fcaf6-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="fcaf6-107">mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti, která je požadována k podpisu.</span><span class="sxs-lookup"><span data-stu-id="fcaf6-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="fcaf6-108">mimo Vyrovnávací paměť, která ukládá podpis.</span><span class="sxs-lookup"><span data-stu-id="fcaf6-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcaf6-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fcaf6-109">Return Value</span></span>  
 <span data-ttu-id="fcaf6-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fcaf6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcaf6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fcaf6-111">Requirements</span></span>  
 <span data-ttu-id="fcaf6-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fcaf6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcaf6-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fcaf6-113">See also</span></span>

- [<span data-ttu-id="fcaf6-114">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fcaf6-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="fcaf6-115">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="fcaf6-115">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="fcaf6-116">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="fcaf6-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
