---
title: 1125 - InvokeMethodIsNotStatic
ms.date: 03/30/2017
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
ms.openlocfilehash: 692c5e56dac0a69ab5705acd284f048391145641
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="1125---invokemethodisnotstatic"></a>1125 - InvokeMethodIsNotStatic
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1125|  
|Klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Během kroku CacheMetadata InvokeMethod aktivity znamená, že metoda k vyvolání není statický.  
  
## <a name="message"></a>Zpráva  
 InvokeMethod '%1' - metoda nejsou statické.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:String|Zobrazovaný název InvokeMethod aktivity.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
