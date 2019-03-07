---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24560ed4b0bb7ca04d5859280baa594fbb2e4097
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473461"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="47677-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="47677-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="47677-103">Nastaví výchozí metodu, která zahájí asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="47677-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47677-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47677-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47677-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47677-105">Parameters</span></span>  
  
|<span data-ttu-id="47677-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="47677-106">Parameter</span></span>|<span data-ttu-id="47677-107">Popis</span><span class="sxs-lookup"><span data-stu-id="47677-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="47677-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="47677-108">Return Value</span></span>  
 <span data-ttu-id="47677-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="47677-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47677-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47677-110">Requirements</span></span>  
 <span data-ttu-id="47677-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="47677-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47677-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47677-112">See also</span></span>
- [<span data-ttu-id="47677-113">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47677-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
