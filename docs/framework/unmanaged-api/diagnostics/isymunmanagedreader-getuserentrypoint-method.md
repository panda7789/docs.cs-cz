---
title: ISymUnmanagedReader::GetUserEntryPoint – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0267ae8b57c837b097d496c8e119085d03417e36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211267"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="eac5e-102">ISymUnmanagedReader::GetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="eac5e-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="eac5e-103">Vrátí metodu, která byla zadána jako uživatel vstupní bod pro modul, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="eac5e-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="eac5e-104">Tato metoda může být například hlavní metoda uživatele spíše než vygenerovaný kompilátorem zástupné procedury před voláním hlavní metody.</span><span class="sxs-lookup"><span data-stu-id="eac5e-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eac5e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eac5e-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eac5e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="eac5e-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="eac5e-107">[out] Ukazovat na proměnnou, která přijímá vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="eac5e-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eac5e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eac5e-108">Return Value</span></span>  
 <span data-ttu-id="eac5e-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="eac5e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eac5e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eac5e-110">Requirements</span></span>  
 <span data-ttu-id="eac5e-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="eac5e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eac5e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eac5e-112">See also</span></span>

- [<span data-ttu-id="eac5e-113">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eac5e-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
