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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796549"
---
# <a name="iassemblyname-interface"></a>IAssemblyName – rozhraní
Poskytuje metody pro popis a práci s jedinečnou identitou sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](iassemblyname-clone-method.md)|Vytvoří kopii tohoto `IAssemblyName` objektu bez podstruktury.|  
|[Finalize – metoda](iassemblyname-finalize-method.md)|Umožňuje tomuto `IAssemblyName` objektu uvolnit prostředky a provést jiné operace čištění před voláním jeho destruktoru.|  
|[GetDisplayName – metoda](iassemblyname-getdisplayname-method.md)|Získá popisný název sestavení, na které odkazuje tento `IAssemblyName` objekt.|  
|[GetName – metoda](iassemblyname-getname-method.md)|Získá jednoduchý, nešifrovaný název sestavení, na který odkazuje tento `IAssemblyName` objekt.|  
|[GetProperty – metoda](iassemblyname-getproperty-method.md)|Získá ukazatel na vlastnost, na kterou odkazuje zadaný `PropertyId`.|  
|[GetVersion – metoda](iassemblyname-getversion-method.md)|Získá informace o verzi sestavení, na které odkazuje tento `IAssemblyName` objekt.|  
|[IsEqual – metoda](iassemblyname-isequal-method.md)|Určuje `IAssemblyName`, zda je `IAssemblyName` zadaný objekt na základě zadaných příznaků porovnávání stejný.|  
|[SetProperty – metoda](iassemblyname-setproperty-method.md)|Nastaví hodnotu vlastnosti, na kterou odkazuje zadaný `PropertyId`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
- [IAssemblyEnum – rozhraní](iassemblyenum-interface.md)
