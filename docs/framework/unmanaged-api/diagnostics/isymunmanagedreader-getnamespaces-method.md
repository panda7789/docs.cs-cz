---
title: ISymUnmanagedReader::GetNamespaces – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
ms.openlocfilehash: 458faedea418e626a6494ca2afcdbf0e034472e8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447730"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="f7bcf-102">ISymUnmanagedReader::GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="f7bcf-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="f7bcf-103">Načte obory názvů definované v globálním oboru v rámci tohoto úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7bcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7bcf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7bcf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7bcf-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="f7bcf-106">pro Velikost pole obory názvů.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="f7bcf-107">mimo Ukazatel na proměnnou, která přijímá délku seznamu oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="f7bcf-108">mimo Ukazatel na proměnnou, která přijímá seznam oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7bcf-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7bcf-109">Return Value</span></span>  
 <span data-ttu-id="f7bcf-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7bcf-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7bcf-111">Requirements</span></span>  
 <span data-ttu-id="f7bcf-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f7bcf-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7bcf-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7bcf-113">See also</span></span>

- [<span data-ttu-id="f7bcf-114">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7bcf-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
