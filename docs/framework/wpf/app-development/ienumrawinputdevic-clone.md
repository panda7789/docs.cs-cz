---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: abc8a6e4780c8fe50afcf1b04f7e14aeb6452704
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949588"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Vytvoří další enumerátor nezpracované vstupní zařízení pomocí stejného stavu jako aktuální enumerátor k iteraci přes stejného seznamu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppenum`  
  
 [out] Adresy výstupní proměnné, která přijímá [ienumrawinputdevice –](ienumrawinputdevice.md) ukazatel rozhraní. Pokud je metoda neúspěšná, hodnota této výstupní proměnné není definována.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HODNOTA HRESULT: Tato metoda podporuje standardní návratové hodnoty E_INVALIDARG E_OUTOFMEMORY a e_unexpected, je.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje zaznamenávat do bodu v pořadí výčtu vraťte do tohoto bodu později. Volající musí uvolnit tento nový čítač odděleně od první enumerátor.
