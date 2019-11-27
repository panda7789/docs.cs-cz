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
