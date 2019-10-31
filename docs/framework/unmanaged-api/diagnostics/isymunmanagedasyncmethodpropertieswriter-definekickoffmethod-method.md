---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: ccf1287a1b0218e7f2560e1afbb0930c93b43263
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129175"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="42159-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="42159-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="42159-103">Nastaví počáteční metodu, která inicializuje asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="42159-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42159-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42159-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42159-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42159-105">Parameters</span></span>  
  
|<span data-ttu-id="42159-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="42159-106">Parameter</span></span>|<span data-ttu-id="42159-107">Popis</span><span class="sxs-lookup"><span data-stu-id="42159-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="42159-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="42159-108">Return Value</span></span>  
 <span data-ttu-id="42159-109">Vrátí `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="42159-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42159-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42159-110">Requirements</span></span>  
 <span data-ttu-id="42159-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="42159-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42159-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42159-112">See also</span></span>

- [<span data-ttu-id="42159-113">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42159-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
