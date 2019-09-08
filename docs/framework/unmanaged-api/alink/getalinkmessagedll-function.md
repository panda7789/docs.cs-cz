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
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll – funkce
Vyhledá a načte knihovnu DLL zpráv. Vrátí hodnotu 0, pokud nebyla nalezena nebo načtena knihovna DLL zpráv. Knihovna DLL zpráv by měla být buď v podadresáři, jejíž název je ID jazyka nebo v aktuálním adresáři.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ALink. h  
  
 **Knihovna**: ALink. dll  
  
## <a name="see-also"></a>Viz také:

- [Al.exe (linker sestavení)](../../tools/al-exe-assembly-linker.md)
