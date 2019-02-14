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
ms.openlocfilehash: b3d7555ec5b87957ff1c8e085a4c3ac44c660b0c
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260813"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo – funkce
Získá poslední kód chyby, která byla vygenerována pomocí jedné z funkcí silného názvu.  
  
 Tato funkce je zastaralá.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameErrorInfo ();   
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Poslední modelu COM. kód chyby: nastavit podle jedné z funkcí silného názvu.  
  
## <a name="remarks"></a>Poznámky  
 Většina metod silného názvu vrátit jednoduchý `true` nebo `false` údaj o úspěšném dokončení. Použití `StrongNameErrorInfo` funkce načtete HRESULT, který určuje poslední chyby generované silného názvu funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
