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
ms.openlocfilehash: 323e53c45a26d5703548ebe9863978f6d3929f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787474"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="3e057-102">GetALinkMessageDll – funkce</span><span class="sxs-lookup"><span data-stu-id="3e057-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="3e057-103">Vyhledá a načte knihovnu DLL zpráv.</span><span class="sxs-lookup"><span data-stu-id="3e057-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="3e057-104">Vrátí hodnotu 0, pokud nebyla nalezena nebo načtena knihovna DLL zpráv.</span><span class="sxs-lookup"><span data-stu-id="3e057-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="3e057-105">Knihovna DLL zpráv by měla být buď v podadresáři, jejíž název je ID jazyka nebo v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="3e057-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e057-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e057-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="3e057-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e057-107">Requirements</span></span>  
 <span data-ttu-id="3e057-108">**Záhlaví:** ALink. h</span><span class="sxs-lookup"><span data-stu-id="3e057-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="3e057-109">**Knihovna**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="3e057-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e057-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e057-110">See also</span></span>

- [<span data-ttu-id="3e057-111">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="3e057-111">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
