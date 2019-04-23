---
title: Nelze zapisovat do souboru protokolu, protože při zápisu by došlo ke snížení volného místa na disku určeného hodnotou ReservedSpace
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
ms.openlocfilehash: 38cba8c01741196de9c316ed137acf750add9e89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308780"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a>Nelze zapisovat do souboru protokolu, protože při zápisu by došlo ke snížení volného místa na disku určeného hodnotou ReservedSpace
<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Třídy nemůže zapisovat do souboru protokolu, protože:  
  
-   Množství volného místa na disku (v bajtech) je menší než hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> vlastnost  
  
     – a –  
  
-   Hodnota <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> byla vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Archivovat protokoly na stávající a neodeberete z počítače, aby <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> objekt k vytvoření nové protokoly.  
  
2. Změňte hodnotu <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> vlastnost na menší hodnotu rezervovat méně místa na disku.  
  
3. Nastavte <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> vlastnost <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> se zahodit zprávy bez upozornění, pokud není k dispozici dostatek volného místa na disku.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
