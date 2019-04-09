---
title: CreateALink – funkce
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b494b8b776f4cb0eb534233c5a03ab2d34a698ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115619"
---
# <a name="createalink-function"></a><span data-ttu-id="0fbf2-102">CreateALink – funkce</span><span class="sxs-lookup"><span data-stu-id="0fbf2-102">CreateALink Function</span></span>
<span data-ttu-id="0fbf2-103">Vytvoří instanci propojovacího programu sestavení a nastaví ukazatel na rozhraní zadané.</span><span class="sxs-lookup"><span data-stu-id="0fbf2-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fbf2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fbf2-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fbf2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fbf2-105">Parameters</span></span>  
  
|<span data-ttu-id="0fbf2-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="0fbf2-106">Parameter</span></span>|<span data-ttu-id="0fbf2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0fbf2-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="0fbf2-108">Fyzický název jedné z propojovacího programu sestavení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0fbf2-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="0fbf2-109">Umístění, které při úspěšném dokončení obsahuje ukazatel `riid` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0fbf2-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0fbf2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0fbf2-110">Requirements</span></span>  
 <span data-ttu-id="0fbf2-111">**Knihovna**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="0fbf2-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fbf2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fbf2-112">See also</span></span>

- [<span data-ttu-id="0fbf2-113">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="0fbf2-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
