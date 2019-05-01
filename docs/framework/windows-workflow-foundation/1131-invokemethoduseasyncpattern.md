---
title: 1131 – InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009952"
---
# <a name="1131---invokemethoduseasyncpattern"></a>1131 – InvokeMethodUseAsyncPattern
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1131|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Během kroku CacheMetadata aktivity InvokeMethod označuje, že používá asynchronní vzorek, při volání metody.  
  
## <a name="message"></a>Zpráva  
 InvokeMethod '%1' - metoda používá asynchronní vzorek '%2' a '%3'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|Zobrazovaný název aktivity InvokeMethod|  
|BeginMethod|xs:string|Název metody begin.|  
|EndMethod|xs:string|Název metody end.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
