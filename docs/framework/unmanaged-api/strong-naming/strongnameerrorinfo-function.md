---
title: StrongNameErrorInfo – funkce
ms.date: 03/30/2017
api_name:
- StrongNameErrorInfo
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameErrorInfo
helpviewer_keywords:
- StrongNameErrorInfo function [.NET Framework strong naming]
ms.assetid: e91bf8c3-7c26-4732-938e-2e5b04abfc99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 021fa1668247bc59a4412d2b5f4bac3f5ee8cc6b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799110"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo – funkce
Získá poslední kód chyby, který byl vyvolán jednou ze všech funkcí se silným názvem.  
  
 Tato funkce je zastaralá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameErrorInfo ();   
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Poslední kód chyby COM nastavený jednou z funkcí silného názvu.  
  
## <a name="remarks"></a>Poznámky  
 Většina metod silného názvu vrací jednoduché `true` nebo `false` náznaky úspěšného dokončení. `StrongNameErrorInfo` Pomocí funkce můžete načíst hodnotu HRESULT, která určuje poslední chybu vygenerovanou funkcemi silného názvu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** StrongName. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
