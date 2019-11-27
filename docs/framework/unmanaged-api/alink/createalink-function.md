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
ms.openlocfilehash: 9165a4db7e65fb0f409a902b06d32e9c2988aa69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446555"
---
# <a name="createalink-function"></a><span data-ttu-id="ff01c-102">CreateALink – funkce</span><span class="sxs-lookup"><span data-stu-id="ff01c-102">CreateALink Function</span></span>
<span data-ttu-id="ff01c-103">Vytvoří instanci linkeru sestavení a nastaví ukazatel na zadané rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ff01c-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff01c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff01c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff01c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff01c-105">Parameters</span></span>  
  
|<span data-ttu-id="ff01c-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="ff01c-106">Parameter</span></span>|<span data-ttu-id="ff01c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ff01c-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="ff01c-108">Fyzický název jednoho z rozhraní linkeru sestavení.</span><span class="sxs-lookup"><span data-stu-id="ff01c-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="ff01c-109">Umístění, které po úspěšném dokončení obsahuje ukazatel na rozhraní `riid`.</span><span class="sxs-lookup"><span data-stu-id="ff01c-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ff01c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff01c-110">Requirements</span></span>  
 <span data-ttu-id="ff01c-111">**Knihovna**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="ff01c-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff01c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff01c-112">See also</span></span>

- [<span data-ttu-id="ff01c-113">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="ff01c-113">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
