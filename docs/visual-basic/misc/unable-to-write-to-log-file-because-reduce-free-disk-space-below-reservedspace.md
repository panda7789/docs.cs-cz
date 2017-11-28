---
title: "Nelze zapisovat do souboru protokolu, protože zápis do něj by snížení volného místa na disku hodnotou ReservedSpace"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0adc3438a9473885022e9785c5381f8da0b6f303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a>Nelze zapisovat do souboru protokolu, protože zápis do něj by snížení volného místa na disku hodnotou ReservedSpace
<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Třída nemůže zapisovat do souboru protokolu, protože:  
  
-   Množství volného místa na disku (v bajtech) je menší než hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> vlastnost  
  
     – a –  
  
-   Hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> byla vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Archivovat existující protokoly a je odebrat z počítače na Povolit <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objekt k vytvoření nové protokoly.  
  
2.  Změňte hodnotu <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> vlastnost na menší hodnotu tak, aby vyhradil méně místa na disku.  
  
3.  Nastavte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> vyřadí zpráv bez upozornění, pokud není k dispozici dostatek volného místa na disku.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 [My.Application.Log – objekt](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [My.log – objekt](../../visual-basic/language-reference/objects/my-log-object.md)
