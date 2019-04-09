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
ms.openlocfilehash: 135ae21c2281c545aa701ac2a22a43cea63f5242
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120325"
---
# <a name="isymunmanagedencupdateinitializeforenc-method"></a><span data-ttu-id="4b541-102">ISymUnmanagedENCUpdate::InitializeForEnc – metoda</span><span class="sxs-lookup"><span data-stu-id="4b541-102">ISymUnmanagedENCUpdate::InitializeForEnc Method</span></span>
<span data-ttu-id="4b541-103">Umožňuje hranice metody vypočítání před prvním volání [isymunmanagedencupdate::updatesymbolstore2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4b541-103">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b541-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b541-104">Syntax</span></span>  
  
```  
HRESULT InitializeForEnc();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4b541-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4b541-105">Return Value</span></span>  
 <span data-ttu-id="4b541-106">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4b541-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b541-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b541-107">Requirements</span></span>  
 <span data-ttu-id="4b541-108">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4b541-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b541-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b541-109">See also</span></span>

- [<span data-ttu-id="4b541-110">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b541-110">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
