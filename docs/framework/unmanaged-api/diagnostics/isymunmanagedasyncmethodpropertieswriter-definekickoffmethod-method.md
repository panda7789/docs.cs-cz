---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce3c135e031d0c8425e990811fedc40f4ec45243
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940111"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="c1a11-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="c1a11-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="c1a11-103">Nastaví výchozí metodu, která zahájí asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="c1a11-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1a11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1a11-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1a11-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1a11-105">Parameters</span></span>  
  
|<span data-ttu-id="c1a11-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="c1a11-106">Parameter</span></span>|<span data-ttu-id="c1a11-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c1a11-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="c1a11-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c1a11-108">Return Value</span></span>  
 <span data-ttu-id="c1a11-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c1a11-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1a11-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1a11-110">Requirements</span></span>  
 <span data-ttu-id="c1a11-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c1a11-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a11-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1a11-112">See also</span></span>

- [<span data-ttu-id="c1a11-113">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1a11-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
