---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="1131---invokemethoduseasyncpattern"></a>1131 - InvokeMethodUseAsyncPattern
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1131|  
|Klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Během kroku CacheMetadata InvokeMethod aktivity signalizuje, že ho vzoru async při volání metody.  
  
## <a name="message"></a>Zpráva  
 InvokeMethod '%1' - metoda používá asynchronní vzor '%2' a '%3'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:String|Zobrazovaný název InvokeMethod aktivity.|  
|BeginMethod|xs:String|Název metody begin.|  
|EndMethod|xs:String|Název metody end.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
