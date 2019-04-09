---
title: GetALinkMessageDll – funkce
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: edd83e62b08aa7892c01577cd8c46f9d965c0894
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163017"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="1b28f-102">GetALinkMessageDll – funkce</span><span class="sxs-lookup"><span data-stu-id="1b28f-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="1b28f-103">Vyhledá a načte knihovna DLL zprávy.</span><span class="sxs-lookup"><span data-stu-id="1b28f-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="1b28f-104">Vrátí hodnotu 0, pokud knihovna DLL zprávy nelze umístěný nebo načíst.</span><span class="sxs-lookup"><span data-stu-id="1b28f-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="1b28f-105">Knihovna DLL zprávy musí být buď v podadresáři, jehož název je ID jazyka, nebo v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="1b28f-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b28f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b28f-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="1b28f-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b28f-107">Requirements</span></span>  
 <span data-ttu-id="1b28f-108">**Záhlaví:** alink.h</span><span class="sxs-lookup"><span data-stu-id="1b28f-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="1b28f-109">**Knihovna**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="1b28f-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b28f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b28f-110">See also</span></span>

- [<span data-ttu-id="1b28f-111">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="1b28f-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
