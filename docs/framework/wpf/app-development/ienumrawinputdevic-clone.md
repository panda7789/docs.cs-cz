---
title: IEnumRAWINPUTDEVIC:Clone
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db218ec824dfe163946b0c1bd412efd0f78f4ad8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Vytvoří další nezpracované vstupní zařízení enumerátor stejného stavu jako aktuální enumerátor Iterujte přes stejný seznam.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppenum`  
  
 [out] Adresa výstup proměnné, která přijímá [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) ukazatel rozhraní. Pokud je metoda úspěšné, hodnotu tento výstup proměnné není definován.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HRESULT: Tato metoda podporuje standardní návratové hodnoty E_INVALIDARG E_OUTOFMEMORY a E_UNEXPECTED.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje zaznamenat bod v pořadí výčtu cílem vrátit do tohoto bodu později. Volající musí uvolnit tento nový enumerátor odděleně od první enumerátor.
