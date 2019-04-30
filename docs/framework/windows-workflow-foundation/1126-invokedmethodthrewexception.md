---
title: 1126 – InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 714a98a300426d80c3b494d701ae1bd53a49592f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924004"
---
# <a name="1126---invokedmethodthrewexception"></a>1126 – InvokedMethodThrewException
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1126|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že došlo k výjimce v metodě volané aktivitou InvokeMethod.  
  
## <a name="message"></a>Zpráva  
 Došlo k výjimce v metodě volané aktivitou '%1'. %2  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|Zobrazovaný název aktivity InvokeMethod|  
|Výjimka|xs:string|Podrobnosti o výjimce pro výjimku|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
