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
ms.openlocfilehash: d5eedc34b75d3a0c02969c06454b0f7ec942ed17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176939"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo – funkce
Získá poslední kód chyby, která byla vyvolána jedním z funkce silného názvu.  
  
 Tato funkce byla zastaralá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StrongNameErrorInfo ();
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Poslední kód chyby COM nastavený jednou z funkcí silného názvu.  
  
## <a name="remarks"></a>Poznámky  
 Většina metod silného názvu `true` `false` vrátí jednoduché nebo označení úspěšného dokončení. Pomocí `StrongNameErrorInfo` funkce načtěte HRESULT, který určuje poslední chybu generovanou funkcemi silného názvu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
