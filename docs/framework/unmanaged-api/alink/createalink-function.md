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
ms.openlocfilehash: 993848711f41c9e03b969a3c611982a5c8bc860d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742217"
---
# <a name="createalink-function"></a><span data-ttu-id="f9fcb-102">CreateALink – funkce</span><span class="sxs-lookup"><span data-stu-id="f9fcb-102">CreateALink Function</span></span>
<span data-ttu-id="f9fcb-103">Vytvoří instanci propojovacího programu sestavení a nastaví ukazatel na rozhraní zadané.</span><span class="sxs-lookup"><span data-stu-id="f9fcb-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9fcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9fcb-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9fcb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9fcb-105">Parameters</span></span>  
  
|<span data-ttu-id="f9fcb-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="f9fcb-106">Parameter</span></span>|<span data-ttu-id="f9fcb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f9fcb-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="f9fcb-108">Fyzický název jedné z propojovacího programu sestavení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f9fcb-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="f9fcb-109">Umístění, které při úspěšném dokončení obsahuje ukazatel `riid` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f9fcb-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9fcb-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9fcb-110">Requirements</span></span>  
 <span data-ttu-id="f9fcb-111">**Knihovna**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="f9fcb-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9fcb-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9fcb-112">See also</span></span>

- [<span data-ttu-id="f9fcb-113">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="f9fcb-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
