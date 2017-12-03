---
title: 1126 - InvokedMethodThrewException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a1021d7d23b8e9c25684da567b769c24380a8a0a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1126---invokedmethodthrewexception"></a>1126 - InvokedMethodThrewException
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1126|  
|Klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že metoda volána aktivitou InvokeMethod došlo k výjimce.  
  
## <a name="message"></a>Zpráva  
 V metodě volá aktivita '%1' došlo k výjimce. %2  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:String|Zobrazovaný název InvokeMethod aktivity.|  
|Výjimka|xs:String|Podrobnosti o výjimce pro výjimky|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
