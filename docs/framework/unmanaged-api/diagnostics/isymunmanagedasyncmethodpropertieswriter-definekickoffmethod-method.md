---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: c35455fc679d79d56814a9c2f026ec395e944f24
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441718"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="7be07-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="7be07-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="7be07-103">Nastaví počáteční metodu, která inicializuje asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="7be07-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7be07-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7be07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7be07-105">Parameters</span></span>  
  
|<span data-ttu-id="7be07-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="7be07-106">Parameter</span></span>|<span data-ttu-id="7be07-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7be07-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="7be07-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7be07-108">Return Value</span></span>  
 <span data-ttu-id="7be07-109">Vrací objekt `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="7be07-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7be07-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7be07-110">Requirements</span></span>  
 <span data-ttu-id="7be07-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7be07-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be07-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="7be07-112">See also</span></span>

- [<span data-ttu-id="7be07-113">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7be07-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
