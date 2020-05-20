---
title: ISymUnmanagedNamespace::GetName – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: 84b2f1226c84713483499c7ff777838058cb0f95
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615108"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="657fc-102">ISymUnmanagedNamespace::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="657fc-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="657fc-103">Získá název tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="657fc-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="657fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="657fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="657fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="657fc-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="657fc-106">pro `ULONG32`Který označuje velikost `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="657fc-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="657fc-107">mimo Ukazatel na `ULONG32` , který obdrží velikost vyrovnávací paměti, která je nutná k uložení názvu oboru názvů, včetně ukončení hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="657fc-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="657fc-108">mimo Ukazatel na vyrovnávací paměť, která obsahuje název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="657fc-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="657fc-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="657fc-109">Return Value</span></span>  
 <span data-ttu-id="657fc-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="657fc-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="657fc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="657fc-111">Requirements</span></span>  
 <span data-ttu-id="657fc-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="657fc-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="657fc-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="657fc-113">See also</span></span>

- [<span data-ttu-id="657fc-114">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="657fc-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
