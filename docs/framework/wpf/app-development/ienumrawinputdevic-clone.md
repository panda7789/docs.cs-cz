---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: a4c5e7db813089d1dd138416ac54dd4be467b87b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355015"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Vytvoří další enumerátor nezpracované vstupní zařízení pomocí stejného stavu jako aktuální enumerátor k iteraci přes stejného seznamu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppenum`  
  
 [out] Adresy výstupní proměnné, která přijímá [ienumrawinputdevice –](ienumrawinputdevice.md) ukazatel rozhraní. Pokud je metoda neúspěšná, hodnota této výstupní proměnné není definována.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HODNOTA HRESULT: Tato metoda podporuje standardní návratové hodnoty E_INVALIDARG E_OUTOFMEMORY a e_unexpected, je.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje zaznamenávat do bodu v pořadí výčtu vraťte do tohoto bodu později. Volající musí uvolnit tento nový čítač odděleně od první enumerátor.
