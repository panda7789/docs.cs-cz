---
title: ISymUnmanagedReader::GetMethodVersion – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76d850363940ff53135fc66ec057ee67822fa40d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424661"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="3e9e4-102">ISymUnmanagedReader::GetMethodVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="3e9e4-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="3e9e4-103">Získá verzi metoda.</span><span class="sxs-lookup"><span data-stu-id="3e9e4-103">Gets the method version.</span></span> <span data-ttu-id="3e9e4-104">Metoda verze začíná na 1 a se zvýší pokaždé, když znovu zkompiluje metodu.</span><span class="sxs-lookup"><span data-stu-id="3e9e4-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="3e9e4-105">Rekompilace může dojít bez změny metody.</span><span class="sxs-lookup"><span data-stu-id="3e9e4-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e9e4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e9e4-106">Syntax</span></span>  
  
```  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e9e4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e9e4-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="3e9e4-108">[v] Metoda, pro které chcete získat verzi.</span><span class="sxs-lookup"><span data-stu-id="3e9e4-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="3e9e4-109">[out] Ukazatel na proměnné, která přijímá metoda verze.</span><span class="sxs-lookup"><span data-stu-id="3e9e4-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e9e4-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3e9e4-110">Return Value</span></span>  
 <span data-ttu-id="3e9e4-111">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3e9e4-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e9e4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e9e4-112">Requirements</span></span>  
 <span data-ttu-id="3e9e4-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3e9e4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9e4-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e9e4-114">See Also</span></span>  
 [<span data-ttu-id="3e9e4-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e9e4-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
