---
title: 1124 – InvokeMethodIsStatic
ms.date: 03/30/2017
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
ms.openlocfilehash: 49a9dec73392681fd4150c611f78399a1e15dd48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924056"
---
# <a name="1124---invokemethodisstatic"></a>1124 – InvokeMethodIsStatic
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1124|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Během kroku metoda CacheMetadata aktivity InvokeMethod značí, že má být volána metoda je statická.  
  
## <a name="message"></a>Zpráva  
 InvokeMethod '%1' - metoda je statická.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|Zobrazovaný název aktivity InvokeMethod|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
