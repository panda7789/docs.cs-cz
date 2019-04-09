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
ms.openlocfilehash: b5d4145e6c76cf95f2468a3f5ad59edcd310423e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160872"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="ddc61-102">ISymUnmanagedReader::GetMethodVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="ddc61-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="ddc61-103">Získá verzi metody.</span><span class="sxs-lookup"><span data-stu-id="ddc61-103">Gets the method version.</span></span> <span data-ttu-id="ddc61-104">Metoda verze začíná 1 a se zvýší pokaždé, když metoda přepsán.</span><span class="sxs-lookup"><span data-stu-id="ddc61-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="ddc61-105">Opětovnou kompilaci může dojít bez změny metody.</span><span class="sxs-lookup"><span data-stu-id="ddc61-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddc61-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddc61-106">Syntax</span></span>  
  
```  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddc61-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddc61-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="ddc61-108">[in] Metoda, u kterého chcete získat verzi.</span><span class="sxs-lookup"><span data-stu-id="ddc61-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="ddc61-109">[out] Ukazovat na proměnnou, která přijímá verze metody.</span><span class="sxs-lookup"><span data-stu-id="ddc61-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddc61-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ddc61-110">Return Value</span></span>  
 <span data-ttu-id="ddc61-111">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ddc61-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddc61-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ddc61-112">Requirements</span></span>  
 <span data-ttu-id="ddc61-113">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ddc61-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddc61-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ddc61-114">See also</span></span>

- [<span data-ttu-id="ddc61-115">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddc61-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
