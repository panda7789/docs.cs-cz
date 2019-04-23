---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 04caca0c580d26fde7fc9a3e3a11b7a8fed26d65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225518"
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
Toto rozhraní zobrazí nezpracované vstupní zařízení a používá se pouze podle PresentationHost.exe.  
  
> [!NOTE]
>  Toto rozhraní API je určen a podporovaných pro použití v místním klientském počítači.  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)|Vytvoří výčet Další `celt` elementy (to znamená, RAWINPUTDEVICE struktury) v seznamu čítače výčtu je vrácení `rgelt` spolu s skutečný počet prvků ve výčtu v `pceltFetched`.|  
|[IEnumRAWINPUTDEVIC:Skip](ienumrawinputdevic-skip.md)|Dává pokyn enumerátorem přeskočit na další `celt` elementy ve výčtu tak, aby na další volání [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) nevrátí tyto elementy.|  
|[IEnumRAWINPUTDEVIC:Reset](ienumrawinputdevic-reset.md)|Návrat na začátek pořadí výčtu.|  
|[IEnumRAWINPUTDEVIC:Clone](ienumrawinputdevic-clone.md)|Vytvoří další enumerátor nezpracované vstupní zařízení pomocí stejného stavu jako aktuální enumerátor k iteraci přes stejného seznamu.|  
  
## <a name="see-also"></a>Viz také:

- [O vstup nezpracovaných dat](/windows/desktop/inputdev/about-raw-input)
