---
title: ICorDebugProcess4 – rozhraní
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 1bdc958f2516bcd7c2eb74312fbf478e6d49535a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948798"
---
# <a name="icordebugprocess4-interface"></a>ICorDebugProcess4 – rozhraní

Poskytuje podporu pro mimo proces řízení provádění.

## <a name="methods"></a>Metody

| Metoda                                                                 | Popis                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) | Upozorní ICorDebug kanálu, že je vzdálený ladicí program procesu pokračovat v provádění od laděného objektu. |

## <a name="remarks"></a>Poznámky

Toto rozhraní se nachází uvnitř modulu runtime a není dostupná záhlaví nebo soubory knihoven. Je však rozhraní modelu COM, která je odvozena z `IUnknown` s identifikátorem GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` , který můžete získat prostřednictvím obvykle COM mechanismů.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** Žádné

**Knihovna:** Žádné

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
