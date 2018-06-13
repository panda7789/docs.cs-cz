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
ms.openlocfilehash: 7b4c334d82320066bf9459907660fe6b7e2acefd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425318"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="e0f69-102">ISymUnmanagedReader::GetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="e0f69-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="e0f69-103">Vrátí metodu, která byla zadána jako vstupní bod uživatele modulu, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="e0f69-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="e0f69-104">Tato metoda může být například hlavní metoda uživatele spíše než generované kompilátorem zástupných procedur před hlavní metodu.</span><span class="sxs-lookup"><span data-stu-id="e0f69-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0f69-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0f69-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0f69-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0f69-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="e0f69-107">[out] Ukazatel na proměnnou, která přijímá vstupní bod.</span><span class="sxs-lookup"><span data-stu-id="e0f69-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0f69-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e0f69-108">Return Value</span></span>  
 <span data-ttu-id="e0f69-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e0f69-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0f69-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0f69-110">Requirements</span></span>  
 <span data-ttu-id="e0f69-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e0f69-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f69-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0f69-112">See Also</span></span>  
 [<span data-ttu-id="e0f69-113">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0f69-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
