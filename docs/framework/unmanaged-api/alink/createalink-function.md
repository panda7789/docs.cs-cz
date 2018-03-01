---
title: "CreateALink – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 54a5afd8ee42fa122f3e18415be0b1d06c2f9302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="createalink-function"></a><span data-ttu-id="c9f10-102">CreateALink – funkce</span><span class="sxs-lookup"><span data-stu-id="c9f10-102">CreateALink Function</span></span>
<span data-ttu-id="c9f10-103">Vytvoří instanci Linker sestavení a nastaví ukazatele k zadanému rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c9f10-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9f10-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9f10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9f10-105">Parameters</span></span>  
  
|<span data-ttu-id="c9f10-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="c9f10-106">Parameter</span></span>|<span data-ttu-id="c9f10-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c9f10-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="c9f10-108">Fyzický název jednomu z rozhraní Linker sestavení.</span><span class="sxs-lookup"><span data-stu-id="c9f10-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="c9f10-109">Umístění, které při úspěšném dokončení obsahuje odkazy `riid` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c9f10-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9f10-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9f10-110">Requirements</span></span>  
 <span data-ttu-id="c9f10-111">**Knihovna**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="c9f10-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f10-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9f10-112">See Also</span></span>  
 [<span data-ttu-id="c9f10-113">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="c9f10-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
