---
title: IAssemblyName – rozhraní
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
ms.openlocfilehash: de49d66667033dfc6918b139f90cd5523661597f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134319"
---
# <a name="iassemblyname-interface"></a>IAssemblyName – rozhraní
Poskytuje metody pro popis a práci s jedinečnou identitou sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](iassemblyname-clone-method.md)|Vytvoří kopii tohoto objektu `IAssemblyName` bez podstruktury.|  
|[Finalize – metoda](iassemblyname-finalize-method.md)|Umožňuje tomuto objektu `IAssemblyName` uvolnit prostředky a provést jiné operace čištění před voláním destruktoru.|  
|[GetDisplayName – metoda](iassemblyname-getdisplayname-method.md)|Získá název sestavení, na které odkazuje tento objekt `IAssemblyName`, do čitelného lidského.|  
|[GetName – metoda](iassemblyname-getname-method.md)|Získá jednoduchý a nešifrovaný název sestavení, na které odkazuje tento objekt `IAssemblyName`.|  
|[GetProperty – metoda](iassemblyname-getproperty-method.md)|Získá ukazatel na vlastnost, na kterou odkazuje zadaný `PropertyId`.|  
|[GetVersion – metoda](iassemblyname-getversion-method.md)|Získá informace o verzi sestavení, na které odkazuje tento objekt `IAssemblyName`.|  
|[IsEqual – metoda](iassemblyname-isequal-method.md)|Určuje, zda je zadaný objekt `IAssemblyName` rovný tomuto `IAssemblyName`na základě zadaných příznaků porovnávání.|  
|[SetProperty – metoda](iassemblyname-setproperty-method.md)|Nastaví hodnotu vlastnosti, na kterou odkazuje zadaný `PropertyId`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
- [IAssemblyEnum – rozhraní](iassemblyenum-interface.md)
