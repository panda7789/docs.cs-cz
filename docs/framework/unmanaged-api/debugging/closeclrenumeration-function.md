---
title: CloseCLREnumeration – funkce
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
ms.openlocfilehash: 1d42292705dae03e9bf1a1555508dfb69cebde82
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132440"
---
# <a name="closeclrenumeration-function"></a>CloseCLREnumeration – funkce
Uzavře všechny platné události průběžného modulu CLR (Common Language Runtime), které se nacházejí v poli popisovačů vrácených [funkcí EnumerateCLRs –](enumerateclrs-function.md), a uvolní paměť pro pole popisovačů a cest řetězců.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pHandleArray`  
 pro Ukazatel na pole obslužných rutin událostí vrácených [funkcí EnumerateCLRs –](enumerateclrs-function.md).  
  
 `pStringArray`  
 pro Ukazatel na pole cest řetězců CLR vrácených [funkcí EnumerateCLRs –](enumerateclrs-function.md).  
  
 `dwArrayLength`  
 pro Hodnota DWORD, která obsahuje velikost (length) `pHandleArray` nebo `pStringArray` (jsou stejné).  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Obslužné rutiny otevřené [funkcí EnumerateCLRs –](enumerateclrs-function.md) jsou uzavřeny a přidělená paměť pro popisovač a pole řetězců jsou uvolněny.  
  
 E_INVALIDARG  
 Délka `pHandleArray` se neshoduje s délkou, která je předána v `dwArrayLength`.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Funkce nemůže uvolnit paměť pro `pHandleArray` a `pStringArray`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim. h  
  
 **Knihovna:** dbgshim. dll  
  
 **Verze .NET Framework:** 3,5 SP1
