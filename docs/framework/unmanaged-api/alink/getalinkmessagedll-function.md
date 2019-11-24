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
ms.openlocfilehash: 63719d0c6e13768e9dc7ed80e52e2a293e32a8a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449340"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="aa385-102">GetALinkMessageDll – funkce</span><span class="sxs-lookup"><span data-stu-id="aa385-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="aa385-103">Finds and loads the message DLL.</span><span class="sxs-lookup"><span data-stu-id="aa385-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="aa385-104">Returns 0 if the message DLL could not be located or loaded.</span><span class="sxs-lookup"><span data-stu-id="aa385-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="aa385-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span><span class="sxs-lookup"><span data-stu-id="aa385-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa385-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa385-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="aa385-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa385-107">Requirements</span></span>  
 <span data-ttu-id="aa385-108">**Header:** alink.h</span><span class="sxs-lookup"><span data-stu-id="aa385-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="aa385-109">**Library**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="aa385-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa385-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa385-110">See also</span></span>

- [<span data-ttu-id="aa385-111">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="aa385-111">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
