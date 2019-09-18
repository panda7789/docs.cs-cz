---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: cd634b4d4a88d83d425b787ed8493f9aa2504988
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053410"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Vytvoří další výčet nezpracovaných vstupních zařízení se stejným stavem, jako je aktuální enumerátor pro iteraci přes stejný seznam.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppenum`  
  
 mimo Adresa výstupní proměnné, která přijímá ukazatel rozhraní [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) . Pokud je metoda neúspěšná, hodnota této výstupní proměnné není definována.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HRESULT Tato metoda podporuje standardní návratové hodnoty E_INVALIDARG, E_OUTOFMEMORY a E_UNEXPECTED.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje zaznamenat bod v sekvenci výčtu, aby bylo možné později vrátit k danému okamžiku. Volající musí vydávat nový enumerátor odděleně od prvního enumerátoru.
