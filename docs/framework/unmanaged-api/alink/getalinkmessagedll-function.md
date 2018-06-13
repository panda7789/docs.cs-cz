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
ms.openlocfilehash: 395dc85ad638e8a790962a4aa38019612c360ce1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402214"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="98138-102">GetALinkMessageDll – funkce</span><span class="sxs-lookup"><span data-stu-id="98138-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="98138-103">Vyhledá a načte zprávy knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="98138-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="98138-104">Vrátí hodnotu 0, pokud nelze umístěný nebo načíst knihovny DLL zpráv.</span><span class="sxs-lookup"><span data-stu-id="98138-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="98138-105">Zpráva knihovny DLL musí být buď v podadresáři, jejíž název je ID jazyka, nebo v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="98138-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98138-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98138-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="98138-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98138-107">Requirements</span></span>  
 <span data-ttu-id="98138-108">**Záhlaví:** alink.h</span><span class="sxs-lookup"><span data-stu-id="98138-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="98138-109">**Knihovna**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="98138-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98138-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="98138-110">See Also</span></span>  
 [<span data-ttu-id="98138-111">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="98138-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
