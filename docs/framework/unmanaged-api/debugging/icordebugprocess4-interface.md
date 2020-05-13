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
ms.openlocfilehash: fcf725ea98fa4351e72cf592f92968ee2233ecb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213579"
---
# <a name="icordebugprocess4-interface"></a>ICorDebugProcess4 – rozhraní

Poskytuje podporu pro vzdálené řízení spouštění procesů.

## <a name="methods"></a>Metody

| Metoda                                                                 | Popis                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [ProcessStateChanged –](icordebugprocess4-processstatechanged-method.md) | Upozorní kanál ICorDebug, že proces ladicího programu mimo proces pokračuje v provádění laděného objektu. |

## <a name="remarks"></a>Poznámky

Toto rozhraní je v modulu runtime a není zveřejněné prostřednictvím hlaviček nebo souborů knihoven. Jedná se však o rozhraní modelu COM, které je odvozeno z `IUnknown` identifikátoru GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` , který lze získat prostřednictvím obvyklých mechanismů modelu COM.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** NTato

**Knihovna:** NTato

**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
