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
ms.openlocfilehash: dd83fc6a7f553b54cc2acd5e9a93d8d58747d75a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141712"
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
 Většina metod silného názvu vrací jednoduchý `true` nebo `false` indikaci úspěšného dokončení. Pomocí funkce `StrongNameErrorInfo` načtěte hodnotu HRESULT, která určuje poslední chybu vygenerovanou funkcemi silného názvu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
