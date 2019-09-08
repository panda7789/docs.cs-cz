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
ms.openlocfilehash: 24f7e2d5a547b78ceb4808feaf581c6f49807cf7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787628"
---
# <a name="createalink-function"></a><span data-ttu-id="0071b-102">CreateALink – funkce</span><span class="sxs-lookup"><span data-stu-id="0071b-102">CreateALink Function</span></span>
<span data-ttu-id="0071b-103">Vytvoří instanci linkeru sestavení a nastaví ukazatel na zadané rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0071b-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0071b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0071b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0071b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0071b-105">Parameters</span></span>  
  
|<span data-ttu-id="0071b-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="0071b-106">Parameter</span></span>|<span data-ttu-id="0071b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0071b-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="0071b-108">Fyzický název jednoho z rozhraní linkeru sestavení.</span><span class="sxs-lookup"><span data-stu-id="0071b-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="0071b-109">Umístění, které po úspěšném dokončení obsahuje ukazatel na `riid` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0071b-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0071b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0071b-110">Requirements</span></span>  
 <span data-ttu-id="0071b-111">**Knihovna**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="0071b-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0071b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0071b-112">See also</span></span>

- [<span data-ttu-id="0071b-113">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="0071b-113">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
