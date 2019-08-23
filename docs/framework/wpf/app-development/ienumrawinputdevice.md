---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 5249d7ea359db5d5c58ae87600f61048b465b4c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964770"
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
Toto rozhraní vytvoří výčet nezpracovaných vstupních zařízení a používá se pouze PresentationHost. exe.  
  
> [!NOTE]
> Toto rozhraní API je zamýšlené a podporované jenom pro použití v místním klientském počítači.  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)|Vytvoří výčet dalších `celt` prvků (tj. RAWINPUTDEVICE struktury) v seznamu enumerátoru a vrátí `rgelt` je spolu se skutečným počtem výčtových prvků v `pceltFetched`.|  
|[IEnumRAWINPUTDEVIC:Skip](ienumrawinputdevic-skip.md)|Instruuje enumerátor pro přeskočení dalších `celt` prvků výčtu, aby další volání [IEnumRAWINPUTDEVIC: Next](ienumrawinputdevic-next.md) nevrátí tyto prvky.|  
|[IEnumRAWINPUTDEVIC:Reset](ienumrawinputdevic-reset.md)|Obnoví posloupnost výčtu na začátek.|  
|[IEnumRAWINPUTDEVIC:Clone](ienumrawinputdevic-clone.md)|Vytvoří další výčet nezpracovaných vstupních zařízení se stejným stavem, jako je aktuální enumerátor pro iteraci přes stejný seznam.|  
  
## <a name="see-also"></a>Viz také:

- [O nezpracovaném vstupu](/windows/desktop/inputdev/about-raw-input)
