---
title: "GetALinkMessageDll – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetALinkMessageDll
api_location: alink.dll
api_type: DLLExport
f1_keywords: GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e87fe5b49a7d939a350d5d0bcb31f79eaaf333c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="7d7d9-102">GetALinkMessageDll – funkce</span><span class="sxs-lookup"><span data-stu-id="7d7d9-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="7d7d9-103">Vyhledá a načte zprávy knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="7d7d9-104">Vrátí hodnotu 0, pokud nelze umístěný nebo načíst knihovny DLL zpráv.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="7d7d9-105">Zpráva knihovny DLL musí být buď v podadresáři, jejíž název je ID jazyka, nebo v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="7d7d9-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d7d9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d7d9-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="7d7d9-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d7d9-107">Requirements</span></span>  
 <span data-ttu-id="7d7d9-108">**Záhlaví:** alink.h</span><span class="sxs-lookup"><span data-stu-id="7d7d9-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="7d7d9-109">**Knihovna**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="7d7d9-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d7d9-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d7d9-110">See Also</span></span>  
 [<span data-ttu-id="7d7d9-111">Al.exe (Linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="7d7d9-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
