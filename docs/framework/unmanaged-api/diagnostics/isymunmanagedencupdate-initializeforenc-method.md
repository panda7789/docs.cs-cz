---
title: ISymUnmanagedENCUpdate::InitializeForEnc – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.InitializeForEnc
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc
helpviewer_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc method [.NET Framework debugging]
- InitializeForEnc method [.NET Framework debugging]
ms.assetid: 796b2154-b53c-4d07-9e67-80fd6064725a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46daf47e8fd478926ff75fa695f277c692679fb6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424960"
---
# <a name="isymunmanagedencupdateinitializeforenc-method"></a><span data-ttu-id="573bf-102">ISymUnmanagedENCUpdate::InitializeForEnc – metoda</span><span class="sxs-lookup"><span data-stu-id="573bf-102">ISymUnmanagedENCUpdate::InitializeForEnc Method</span></span>
<span data-ttu-id="573bf-103">Umožňuje metoda hranice počítaný před prvním volání [isymunmanagedencupdate::updatesymbolstore2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="573bf-103">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="573bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="573bf-104">Syntax</span></span>  
  
```  
HRESULT InitializeForEnc();  
```  
  
## <a name="return-value"></a><span data-ttu-id="573bf-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="573bf-105">Return Value</span></span>  
 <span data-ttu-id="573bf-106">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="573bf-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="573bf-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="573bf-107">Requirements</span></span>  
 <span data-ttu-id="573bf-108">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="573bf-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="573bf-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="573bf-109">See Also</span></span>  
 [<span data-ttu-id="573bf-110">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="573bf-110">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
