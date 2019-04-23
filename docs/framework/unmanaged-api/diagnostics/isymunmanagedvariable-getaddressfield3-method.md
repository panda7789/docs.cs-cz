---
title: ISymUnmanagedVariable::GetAddressField3 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8b03b96c8cab43046d109d0dd11ae135cb70c9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163602"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="99ad0-102">ISymUnmanagedVariable::GetAddressField3 – metoda</span><span class="sxs-lookup"><span data-stu-id="99ad0-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="99ad0-103">Získá pole třetí adresa pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="99ad0-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="99ad0-104">Její význam závisí na druhu adresu.</span><span class="sxs-lookup"><span data-stu-id="99ad0-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99ad0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99ad0-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99ad0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="99ad0-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="99ad0-107">[out] Ukazatel `ULONG32` , který přijímá pole třetí adresa.</span><span class="sxs-lookup"><span data-stu-id="99ad0-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99ad0-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="99ad0-108">Return Value</span></span>  
 <span data-ttu-id="99ad0-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="99ad0-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99ad0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99ad0-110">Requirements</span></span>  
 <span data-ttu-id="99ad0-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="99ad0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ad0-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99ad0-112">See also</span></span>

- [<span data-ttu-id="99ad0-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99ad0-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="99ad0-114">GetAddressField1 – metoda</span><span class="sxs-lookup"><span data-stu-id="99ad0-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="99ad0-115">GetAddressField2 – metoda</span><span class="sxs-lookup"><span data-stu-id="99ad0-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="99ad0-116">GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="99ad0-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
